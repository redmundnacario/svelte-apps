<script>
    import { createEventDispatcher } from  'svelte'
    const dispatch = createEventDispatcher()
    let player = {
        name : "",
        points : 0
    }
    const addPlayer = (e) => {
        e.preventDefault()
        dispatch("addPlayerDispatch", player)

        // back to default
        player = {
            name :"",
            points : 0
        }
    }
</script>

<div>
    <h2>New Player Form</h2>
    <form on:submit={addPlayer}>
        <input type="text" bind:value={player.name}/>
        <input type="number" bind:value={player.points} />
        <button type="submit" class="btn btn-primary">Add</button>
    </form>
</div>