<script>
    import {createEventDispatcher} from 'svelte';
    export let task = 'test';
    const dispatch = createEventDispatcher();


    function addTask(){
        dispatch('add');
    }
</script>

<input type="text" bind:value="{task}">
<button on:click="{addTask}">Add</button>
