<script>
    import { json } from 'd3-fetch';
    import Scpl from './Scatterplot.svelte'

    let data = null;
    onMount(async () => {
        console.log("onMount started!");
        data = await json('/data/gapminder.json');
        console.log("Data loaded!");
    });
</script>
