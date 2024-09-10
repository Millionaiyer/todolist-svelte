<script>
    import Button from "./Button.svelte";

    export let todos = [];
    let inputText = "";

    const handleToDo = () => {
        if (!inputText) return;
        // console.log(inputText)
    };
</script>

<div>
    {#each todos as { id, title }, index (id)}
        {@const number = index + 1}
        <li>
            {number} - {title}
        </li>
    {/each}

    <form on:submit|preventDefault={handleToDo}>
        <input bind:value={inputText} />
        <!-- <Button type='submit' disabled={true}>Click me</Button> -->
        <Button 
        type="Submit" 
        disabled={!inputText} 
        on:click={() => console.log('hello')}
      >Click</Button>
      
    </form>
</div>
