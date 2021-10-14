<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	let newGoal = '';
	let goals = [];
	function addGoal() {

	}
</script>

<svelte:head>
	<title>Goals</title>
</svelte:head>

<section>
	<label>Goals</label>

	<input bind:value={newGoal}/>

	<button on:click={addGoal}>Add Goal</button>
</section>

<style>

</style>
