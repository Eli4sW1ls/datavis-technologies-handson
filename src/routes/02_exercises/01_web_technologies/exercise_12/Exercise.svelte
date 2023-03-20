<script>
	let clicked = false;
	const msg_t = "You have clicked the button!";
	const msg_f = "You have to click the button!";
</script>

<div>
	<button class="btn btn-primary" on:click={() => (clicked = true)}>
		click here
	</button>
	
	<p>
	{#if clicked}
		{msg_t}
	{:else}
		{msg_f}
	{/if}
	</p>
</div>
