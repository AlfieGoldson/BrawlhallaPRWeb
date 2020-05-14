<script>
  import PlayerItem from "./components/PlayerItem.svelte";
  import Sidebar from "./components/Sidebar.svelte";

  import NA1v1 from "./pr/NA 1v1 - Spring 2020.json";
  import NA2v2 from "./pr/NA 2v2 - Spring 2020.json";

  import EU1v1 from "./pr/EU 1v1 - Spring 2020.json";
  import EU2v2 from "./pr/EU 2v2 - Spring 2020.json";

  import SEA1v1 from "./pr/SEA 1v1 - Spring 2020.json";
  import SEA2v2 from "./pr/SEA 2v2 - Spring 2020.json";

  import SA1v1 from "./pr/SA 1v1 - Spring 2020.json";
  import SA2v2 from "./pr/SA 2v2 - Spring 2020.json";

  import AUS1v1 from "./pr/AUS 1v1 - Spring 2020.json";
  import AUS2v2 from "./pr/AUS 2v2 - Spring 2020.json";

  let region = "NA";
  let bracket = "1v1";
  let search = "";
  let sort = "totalPoints";

  const prs = {
    NA: {
      "1v1": NA1v1,
      "2v2": NA2v2
    },
    EU: {
      "1v1": EU1v1,
      "2v2": EU2v2
    },
    SEA: {
      "1v1": SEA1v1,
      "2v2": SEA2v2
    },
    SA: {
      "1v1": SA1v1,
      "2v2": SA2v2
    },
    AUS: {
      "1v1": AUS1v1,
      "2v2": AUS2v2
    }
  };

  const sortFn = (property, asc = true) => (a, b) => {
    return (a[property] - b[property]) * (asc ? -1 : 1);
  };
</script>

<style>
  main {
    text-align: center;
    display: grid;
    grid-template-columns: 1fr;
    overflow: hidden;
    height: 100vh;
  }
  .sidebar-container {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: none;
  }
  #prTable {
    overflow-y: scroll;
  }
  input {
    flex: 1;
  }
  #prTable header {
    position: sticky;
    top: 0;
    background-color: #0e3e5b;
    color: white;
    text-transform: uppercase;
    z-index: 10;
    box-shadow: 0 0 8px rgba(0, 0, 0, 0.12);
    padding: 0.75rem 0;
  }
  .prRow {
    display: grid;
    grid-template-columns: 6rem 1fr repeat(3, 5rem) 8rem;
    align-items: center;
    padding: 0.25rem 0;
  }

  .prRow label {
    cursor: pointer;
    padding: 0.5rem 0;
  }
  .prRow label:hover {
    background-color: #0b283f;
  }
  .prRow label.active {
    background-color: #dd7917;
  }
  .prContent .prRow {
    border-bottom: 1px solid rgba(14, 62, 91, 0.12);
    color: white;
  }
  .prContent .prRow:nth-of-type(2n) {
    background-color: #0e3e5b;
  }
  .prContent .prRow:nth-of-type(2n + 1) {
    background-color: #0b283f;
  }
  .prContent .prRow:hover {
    background-color: #dd7917;
  }
  input[type="radio"] {
    display: none;
  }
  .t2,
  .t3 {
    display: none;
  }
  @media only screen and (min-width: 1200px) {
    main {
      grid-template-columns: 320px 1fr;
    }
    .sidebar-container {
      position: relative;
      display: block;
    }
    .prRow {
      grid-template-columns: 6rem 1fr repeat(5, 5rem) 8rem;
    }
    .t2,
    .t3 {
      display: block;
    }
  }
</style>

<main>
  <div class="sidebar-container">
    <Sidebar
      {search}
      {bracket}
      {region}
      on:search={e => {
        search = e.detail;
      }}
      on:changeRegion={e => {
        region = e.detail;
      }}
      on:changeBracket={e => {
        bracket = e.detail;
      }} />
  </div>
  <div id="prTable">
    <header class="prRow">
      <p>Rank</p>
      <p style="text-align: left;">Name</p>
      <input type="radio" bind:group={sort} value="t1" id="sort_t1" />
      <label for="sort_t1" class="t1" class:active={sort === 't1'}>Top 1</label>
      <input type="radio" bind:group={sort} value="t2" id="sort_t2" />
      <label for="sort_t2" class="t2" class:active={sort === 't2'}>Top 2</label>
      <input type="radio" bind:group={sort} value="t3" id="sort_t3" />
      <label for="sort_t3" class="t3" class:active={sort === 't3'}>Top 3</label>
      <input type="radio" bind:group={sort} value="t8" id="sort_t8" />
      <label for="sort_t8" class="t8" class:active={sort === 't8'}>Top 8</label>
      <input type="radio" bind:group={sort} value="t32" id="sort_t32" />
      <label for="sort_t32" class="t32" class:active={sort === 't32'}>
        Top 32
      </label>
      <input
        type="radio"
        bind:group={sort}
        value="totalPoints"
        id="sort_points" />
      <label for="sort_points" class:active={sort === 'totalPoints'}>
        Points
      </label>
    </header>
    <div class="prContent">
      {#each prs[region][bracket].sort(sortFn(sort, true)) as player, i}
        {#if player.name.toLowerCase().startsWith(search.toLowerCase())}
          <div class="prRow playerItem">
            <PlayerItem
              player={{ ...player, rank: sort === 'points' ? player.pr : i + 1 }} />
          </div>
        {/if}
      {/each}
    </div>
  </div>
</main>
