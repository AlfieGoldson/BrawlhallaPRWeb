<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  export let search, region, bracket;

  $: dispatch("search", search);
  $: dispatch("changeRegion", region);
  $: dispatch("changeBracket", bracket);
</script>

<style>
  .sidebar {
    display: flex;
    flex-direction: column;
    align-items: stretch;
    background-color: white;
  }
  label.sectionTitle {
    text-transform: uppercase;
    font-size: 1.25rem;
    color: #0e3e5b;
    margin-top: 1rem;
    padding-left: 1rem;
    text-align: left;
  }
  #search {
    padding: 0.5rem;
    font-size: 1rem;
    margin: 0 1rem;
    border: 1px solid #0e3e5b;
  }
  .selectLabel {
    padding: 0.5rem 1rem;
    cursor: pointer;
    display: block;
    text-align: left;
    border-bottom: 1px solid rgba(14, 62, 91, 0.12);
  }
  .selectLabel:hover {
    background-color: #eee;
  }
  input[type="radio"]:checked + label {
    background-color: #0e3e5b;
    color: white;
  }
  #logo {
    width: 100%;
    height: auto;
  }
  input[type="radio"] {
    display: none;
  }
</style>

<div class="sidebar">
  <img src="imgs/Year5Graphic_WEB.png" alt="logo" id="logo" />
  <h1>{region} {bracket} PR</h1>
  <label for="search" class="sectionTitle">Search:</label>
  <input id="search" bind:value={search} />

  <label for="search" class="sectionTitle">Bracket:</label>

  <input type="radio" bind:group={bracket} value="1v1" id="bracket_1v1" />
  <label class="selectLabel" for="bracket_1v1">1v1</label>
  <input type="radio" bind:group={bracket} value="2v2" id="bracket_2v2" />
  <label class="selectLabel" for="bracket_2v2">2v2</label>

  <label for="search" class="sectionTitle">Region:</label>

  <input type="radio" bind:group={region} value="NA" id="region_NA" />
  <label class="selectLabel" for="region_NA">NA</label>
  <input type="radio" bind:group={region} value="EU" id="region_EU" />
  <label class="selectLabel" for="region_EU">EU</label>
  <input type="radio" bind:group={region} value="SA" id="region_SA" />
  <label class="selectLabel" for="region_SA">SA</label>
  <input type="radio" bind:group={region} value="SEA" id="region_SEA" />
  <label class="selectLabel" for="region_SEA">SEA</label>
  <input type="radio" bind:group={region} value="AUS" id="region_AUS" />
  <label class="selectLabel" for="region_AUS">AUS</label>
</div>
