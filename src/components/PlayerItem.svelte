<script>
  export let player;
</script>

<style>
  .pr {
    text-align: center;
  }

  .name {
    font-size: 1.25rem;
    font-weight: bold;
    text-align: left;
    /* cursor: pointer; */
  }

  .top {
    font-size: 1rem;
    text-align: center;
  }

  .points {
    text-align: center;
    font-weight: bold;
  }
</style>

<p class="pr">{player.pr}</p>
<p class="name">{player.name}</p>
<p class="top">{player.t1}</p>
<p class="top">{player.t2}</p>
<p class="top">{player.t3}</p>
<p class="top">{player.t8}</p>
<p class="top">{player.t32}</p>
<p class="top points">{parseFloat(player.totalPoints).toFixed(2)}</p>
