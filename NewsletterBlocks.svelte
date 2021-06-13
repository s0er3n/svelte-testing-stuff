<script>
  export let data;
</script>

<style>
					input {
					  border: 0;
					  background-color: lightgrey;
					  border-radius: 10px;
					  padding: 8px;
					  margin-top: 5px;
					}
</style>

{#each data.blocks as block}
<h1>
{block.subreddit}
</h1>
<div>
		<input bind:value={block.upvoteRatio} >
		<input bind:value={block.subreddit} >
		<input bind:value={block.flairs} >
		<input bind:value={block.count} >
</div>

{/each}