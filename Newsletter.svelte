<script>
	import NewsletterBlocks from "./NewsletterBlocks.svelte";
	let count = 0;
	export let data;
	let clicked = false;
	function handleHover() {
	  clicked = !clicked;
	}
	function handleSubmit() {
	  alert("stuff");
	}
</script>

<style>
	div {
	  background: darkcyan;
	  color: white;
	  font-size: 20px;
	  border: none;
	  padding: 8px 12px;
	  margin: 10px;
	  border-radius: 10px;
	  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
	}
</style>

<div on:click={handleHover}>
  {data.id} 
	{#each data.blocks as block}
	{block.subreddit}
	{/each}

</div>

{#if clicked}
	<NewsletterBlocks {data}/>
	<button on:click={(e) => { handleSubmit();e.preventDefault()}}>
	 submit
	</button>
{/if}


