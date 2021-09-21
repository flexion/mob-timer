<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	const TOTAL_TIME: number = 5;
	let timeRemaining: number = 0;
	let timer: NodeJS.Timer = null;
	let isRunning = false;

	function createTimer() {
		timer = setInterval(() => {
			timeRemaining -= 1;
			if (timeRemaining == 0) {
				isRunning = false;
				clearInterval(timer);
				setTimeout(() => alert('time is up, rotate drivers!'));
			}
		}, 1000)
	}

	function start() {
		isRunning = true;
		timeRemaining = TOTAL_TIME;
		createTimer();
	}

	function pause() {
		isRunning = false;
		clearInterval(timer);
	}

	function resume() {
		createTimer();
		isRunning = true;
	}
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<section>
	<h1>
		Mob Timer
	</h1>
	<h2>
		{timeRemaining}
	</h2>
	{#if timeRemaining === 0}
		<button on:click={start}>start</button>
	{/if}

	{#if timeRemaining > 0 && !isRunning}
		<button on:click={resume}>resume</button>
	{/if}

	{#if isRunning}
		<button on:click={pause}>pause</button>
	{/if}
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
	}
</style>
