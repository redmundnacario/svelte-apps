<script>
	import Navbar from './Navbar.svelte'
	import Player from './Player.svelte'
	import AddPlayer from './AddPlayer.svelte'


	let players = [
			{
				name : "Red",
				points : 28
			},
			{
				name : "Margs",
				points : 29
			},
			{
				name : "Sample",
				points : 10
			},
		]
	
	const addPlayer = (e) => {
		const player = e.detail
		players = [...players, player]
	}
	const removePlayer = (e) => {
		players = players.filter(player => player.name !== e.detail)
	}
</script>
	
<Navbar/>
<div class="container">
	<AddPlayer on:addPlayerDispatch={addPlayer}/>
	{#if players.length === 0 }
	<p>No players loaded.</p>
	{:else}
		{#each players as player}
			<Player 
				name={player.name} 
				points ={player.points}
				on:removePlayer = {removePlayer}
				/>
		{/each}
	{/if}
</div>
