<script>
  let current = "";
</script>

<!-- We will cover buttons later on! -->
<button class="btn btn-secondary" class:clicked={current=="messi"} on:click={() => (current = "messi")}>
  Messi
</button>

<button class="btn btn-secondary" class:clicked={current=="ronaldo"} on:click={() => (current = "ronaldo")}>
  Ronaldo
</button>

<button class="btn btn-secondary" class:clicked={current=="neymar"} on:click={() => (current = "neymar")}>
  Neymar
</button>


<style>
  .clicked {
    background-color: coral;
  }
</style>