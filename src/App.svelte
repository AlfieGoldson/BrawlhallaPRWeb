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
</script>

<style>
  main {
    text-align: center;
    display: grid;
    grid-template-columns: 320px 1fr;
    overflow: hidden;
    height: 100vh;
  }
  #prTable {
    overflow-y: scroll;
  }
  input {
    flex: 1;
  }
  .inputs {
    display: flex;
    margin: 1rem auto;
    justify-content: center;
    max-width: 1200px;
  }
  #prTable header {
    position: sticky;
    top: 0;
    background-color: #0e3e5b;
    color: white;
    text-transform: uppercase;
    padding: 1.25rem 0;
    z-index: 10;
    box-shadow: 0 0 8px rgba(0, 0, 0, 0.12);
  }
  .prRow {
    display: grid;
    grid-template-columns: 6rem 1fr repeat(5, 5rem) 8rem;
    align-items: center;
    padding: 0.25rem 0;
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
</style>

<main>
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
  <div id="prTable">
    <header class="prRow">
      <p>Rank</p>
      <p>Name</p>
      <p>Top 1</p>
      <p>Top 2</p>
      <p>Top 3</p>
      <p>Top 8</p>
      <p>Top 32</p>
      <p>Points</p>
    </header>
    <div class="prContent">
      {#each prs[region][bracket] as player}
        {#if player.name.toLowerCase().startsWith(search.toLowerCase())}
          <div class="prRow">
            <PlayerItem {player} />
          </div>
        {/if}
      {/each}
    </div>
  </div>
</main>
