<script>
  export let player;
</script>

<style>
  .rank {
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
  .t2,
  .t3 {
    display: none;
  }
  @media only screen and (min-width: 1200px) {
    .t2,
    .t3 {
      display: block;
    }
  }
</style>

<p class="rank">{player.rank}</p>
<p class="name">{player.name}</p>
<p class="top t1">{player.t1}</p>
<p class="top t2">{player.t2}</p>
<p class="top t3">{player.t3}</p>
<p class="top t8">{player.t8}</p>
<p class="top t32">{player.t32}</p>
<p class="top points">{parseFloat(player.totalPoints).toFixed(2)}</p>
