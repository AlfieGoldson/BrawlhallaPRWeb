<script>
  import PlayerItem from "./components/PlayerItem.svelte";

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

  let region = "EU";
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
  }
  input {
    width: 100%;
    max-width: 1200px;
  }
  table {
    border-spacing: 0;
  }
</style>

<main>
  <h1>{region} {bracket} PR</h1>
  <input bind:value={search} />
  <select name="region" id="region" bind:value={region}>
    <option value="NA">NA</option>
    <option value="EU">EU</option>
    <option value="SA">SA</option>
    <option value="SEA">SEA</option>
    <option value="AUS">AUS</option>
  </select>
  <select name="bracket" id="bracket" bind:value={bracket}>
    <option value="1v1">1v1</option>
    <option value="2v2">2v2</option>
  </select>
  <table style="width:100%">
    <tr>
      <th>Rank</th>
      <th style="text-align: left">Name</th>
      <th>Top 1</th>
      <th>Top 2</th>
      <th>Top 3</th>
      <th>Top 8</th>
      <th>Top 32</th>
      <th>Points</th>
    </tr>
    {#each prs[region][bracket] as player}
      {#if player.name.toLowerCase().startsWith(search.toLowerCase())}
        <PlayerItem {player} />
      {/if}
    {/each}
  </table>
</main>
