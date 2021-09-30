<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	import { totalTime } from "../stores/timer";
</script>

<svelte:head>
	<title>Settings</title>
</svelte:head>

<section>
	<label>Timer Duration (In Minutes)</label>
	<input type="number" min="1" bind:value={$totalTime} />
</section>

<style>

</style>
