<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	let newGoal = '';
	let goals = [];

	function addGoal() {
		goals = [...goals, {
			text: newGoal,
			isDone: false
		}];
		newGoal = '';
	}

	function deleteGoal(goal) {
		goals.splice(goals.indexOf(goal), 1);
		goals = goals;
	}
</script>

<svelte:head>
	<title>Goals</title>
</svelte:head>

<section>
	<h4>Goals</h4>

	<input bind:value={newGoal}/>

	<button on:click={addGoal}>Add Goal</button>

	<ul>
		{#each goals as goal}
			<li><input bind:checked={goal.isDone} type="checkbox" />
				{goal.text}
				<button on:click={() => deleteGoal(goal)}>X</button>
			</li>
		{/each}
	</ul>
</section>

<style>

</style>
