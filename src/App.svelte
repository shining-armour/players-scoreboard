<svelte:head>
	<title>Players Scoreboard</title>
</svelte:head>

<script>
  /* Importing custom files */
  import Navbar from './Navbar.svelte';
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';
	let players = [
	{
		name: 'Christiano Ronaldo',
		points: 567
	},
	{
		name: 'Sara Williams',
		points: 800
	},
	{
		name: 'Mary Kom',
		points: 768
	}
	];

	const addPlayer = (e) => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	};

	const removePlayer =(e) => {
		players = players.filter(player => player.name !== e.detail);
	}
</script>

<main>
 <Navbar />
 <div class="container">
  <AddPlayer on:addplayer={addPlayer}/>
  {#if players.length === 0}
	<p>No Players</p>
	{:else}
	  {#each players as i}
	    <Player name={i.name} points={i.points} on:removeplayer={removePlayer}/>
	  {/each}
	{/if}
 </div>
</main>

<style>
  .container{
		width: 70%;
		margin: 0 auto;
	}
</style>
