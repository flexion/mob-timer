<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">

	enum TIMER_STATE {
		NEW,
		RUNNING,
		PAUSED
	}

	const TOTAL_TIME: number = 5;
	let timeRemaining: number = 0;
	let timer: NodeJS.Timer = null;
	let timerState: TIMER_STATE = TIMER_STATE.NEW;

	function createTimer() {
		timer = setInterval(() => {
			timeRemaining -= 1;
			if (timeRemaining == 0) {
				timerState = TIMER_STATE.NEW;
				clearInterval(timer);
				setTimeout(() => alert('time is up, rotate drivers!'));
			}
		}, 1000)
	}

	function start() {
		timerState = TIMER_STATE.RUNNING;
		timeRemaining = TOTAL_TIME;
		createTimer();
	}

	function pause() {
		timerState = TIMER_STATE.PAUSED;
		clearInterval(timer);
	}

	function resume() {
		createTimer();
		timerState = TIMER_STATE.RUNNING;
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

	{#if timerState === TIMER_STATE.NEW}
		<button on:click={start}>start</button>
	{/if}

	{#if timerState === TIMER_STATE.PAUSED}
		<button on:click={resume}>resume</button>
	{/if}

	{#if timerState === TIMER_STATE.RUNNING}
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
