<script>
    import Button from "./Button.svelte";
    import { createEventDispatcher } from "svelte";

    export let toDos = [];
    let inputText = "";

    const dispatch = createEventDispatcher();

    const handleAddToDo = () => {
        const isNotCancelled = dispatch(
            "addToDo",
            {
                title: inputText,
            },
            { cancelable: true },
        );
        inputText = '';
        if (isNotCancelled) {
            console.log("yolo ");
        }
    };
    const removeToDo = (id) => {
        dispatch('removeToDo',{
            id
        })
    }

    const handleToggleToDO = (id,value) => {
        dispatch('toggleToDo',{
            id,value
        })
    }
</script>

<div>
    {#each toDos as { id, title,completed } (id)}
        <li>
            <label>
                <input on:input={(event) => {
                    event.currentTarget.checked=completed;
                    handleToggleToDO(id,!completed)
                }} type="checkbox" name="" id="" checked={completed}>
                {title}
            </label> 
            <button on:click={() => removeToDo(id)}>remove</button>
        </li>
    {/each}

    <form on:submit|preventDefault={handleAddToDo}>
        <input bind:value={inputText} />
        <Button type="Submit" disabled={!inputText}>Click</Button>
    </form>
        
</div>
