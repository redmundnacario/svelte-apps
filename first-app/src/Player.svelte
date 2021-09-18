<script>
    import { createEventDispatcher } from 'svelte'

    const dispatch = createEventDispatcher()

	export let name;
	export let points;
	let showControls = false

	const addPoint = () => points ++
	const subtractPoint = () => {
		if (points > 0) {
			points --
		}
	}
	const toggleShowControls = () => { showControls = !showControls}
    const removePlayer = () => dispatch("removePlayer", name)
</script>


<div class="card">
    <div class="card-header-cont">
        <h1>{name}</h1>
        <div>
            <button class="btn btn-light" on:click={toggleShowControls}>
                {#if showControls}-{:else}+{/if}	
            </button>
            <button on:click={removePlayer} class="btn btn-danger">x</button>
        </div>
    </div>
    <h3>Points: {points}</h3>
    {#if showControls}
        <div class="btn-container">
            <button class="btn btn-primary" on:click={addPoint}>+ 1</button>
            <button class="btn btn-danger" on:click={subtractPoint}>- 1</button>
        </div>
        <input type="number" bind:value={points}>
    {/if}
</div>


<style>
	.card-header-cont{
		display: flex;
		justify-content: space-between;
	}
	.btn-container{
		display: flex;
		justify-content: end;
	}
</style>