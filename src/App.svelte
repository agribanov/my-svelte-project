<script>
	let name = 'Alex';

	let tasks = [
		'Wake up',
		'get some coffee',
		'code'
	];

	let task = '';

	function addTask(){
		tasks = [...tasks, task];
		task = '';
	}

</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {name}!</h1>
<input type="text" bind:value="{name}">

<ul>
	{#each tasks as task}
		<li>{task}</li>
		{:else}
		<li>Nothing there</li>
	{/each}
</ul>
<input type="text" bind:value="{task}"><button on:click="{addTask}">Add</button>
