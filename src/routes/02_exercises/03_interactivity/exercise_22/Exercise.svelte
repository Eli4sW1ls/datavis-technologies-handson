<script>
    let ctr = 0;

    function clicked(event) {
        ctr += 1;
    }

    function reset(event) {
        ctr = 0;
    }
    
</script>

<button on:click={clicked} class="btn btn-primary">Clicked: {ctr}</button> 
<button on:click={reset} class="btn btn-danger">Reset</button>