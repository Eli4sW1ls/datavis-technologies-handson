<script>
    import { json } from "d3-fetch";
    import Scpl from './Scatterplot.svelte'
    import { onMount } from 'svelte';

    export let data = null;
    onMount(async () => {
        console.log("onMount started!");
        const ldata = await json('/data/gapminder.json');
        console.log("Data loaded!");
        data = ldata.filter(function (item) {return item.year == 1800});
        console.log(data)
    });
    
    console.log("script done ");
</script>

{#if data == null}
    Data loading...
{:else}
    <Scpl data={data}/>
{/if}