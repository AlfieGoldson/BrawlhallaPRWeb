<script>
  export let player;
</script>

<style>
  tr {
    /* padding: 0.25rem 0.5rem; */
    border-bottom: 1px solid #ccc;
  }

  tr:hover {
    background-color: #eee;
  }

  .pr {
    opacity: 0.8;
    margin-right: 1rem;
    text-align: center;
  }

  .name {
    font-size: 1.5rem;
    font-weight: bold;
    text-align: left;
    cursor: pointer;
  }

  .top {
    font-size: 1rem;
    text-align: center;
  }
</style>

<tr>
  <td class="pr">{player.pr}</td>
  <td class="name">{player.name}</td>
  <td class="top">{player.t1}</td>
  <td class="top">{player.t2}</td>
  <td class="top">{player.t3}</td>
  <td class="top">{player.t8}</td>
  <td class="top">{player.t32}</td>
  <td class="top">{parseFloat(player.totalPoints).toFixed(2)}</td>
</tr>
