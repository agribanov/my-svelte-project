<script>
	import {scale, fly} from 'svelte/transition'
	import Form from './Form.svelte';
	import Quote from './Quote.svelte';

	let name = 'Alex';

	let tasks = [
		'Wake up',
		'get some coffee',
		'code'
	];

	let isQuotesVisible = false;

	$: message = tasks.length ? `You have ${tasks.length} tasks` : 'You have no tasks';

	function addTask(e){
		tasks = [...tasks, e.detail];
	}

</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {name}!</h1>
<input type="text" bind:value="{name}">
<hr />
{message}
<ul>
	{#each tasks as task}
		<li>{task}</li>
		{:else}
		<li>Nothing there</li>
	{/each}
</ul>
<Form on:add="{addTask}"/>
<hr />
<button on:click="{() => isQuotesVisible = !isQuotesVisible}">Toggle Quotes</button>
{#if isQuotesVisible}
	<div in:scale="{{duration:1000}}" out:fly="{{duration: 500, y: 50}}">
		<Quote>Best Quote</Quote>
	</div>
{/if}