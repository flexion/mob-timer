<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	let totalTime: number = 5;

	
</script>

<svelte:head>
	<title>Settings</title>
</svelte:head>

<section>
	<input type="number" min="1" bind:value={totalTime} />
</section>

<style>

</style>
