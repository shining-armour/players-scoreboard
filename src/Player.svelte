<script>
import {createEventDispatcher} from 'svelte';
const dispatch = createEventDispatcher();
/* Exporting and defining variables */
export let name;
export let points;
let showControls = false;
/* Defining functions */
const addPoint = () => points+=1;
const delPoint = () => points-=1;
const toggleControls = () => (showControls = !showControls);
const onDelete = () => {
  var userConfirm = confirm('Do you really want to remove this player?');
  if(userConfirm == true){dispatch("removeplayer", name);};
};
</script>

<main>
 <div class="card">
  <h2>
	  Player : {name}
	  <button class="btn-toggle" on:click={toggleControls}>
	    {#if showControls} - {:else}+{/if}
		</button>
    <button class="btn-danger" on:click={onDelete}>x</button>
	</h2>
  <h3>Points : {points}</h3>
	{#if showControls}
	<button class="btn-add" on:click={addPoint}>+1</button>
	<button class="btn-del" on:click={delPoint}>-1</button>
	<input type="number" bind:value={points}/>
	{/if}
 </div>
</main>

<style>
	.card{
		border: 1px solid #525252;
		border-radius: 5px;
		padding: 20px;
		margin: 10px;
	}
	h2 {
		color: #204f6e;
		margin-bottom: 0;
	}
	h3{
		margin-top:0;
	}
  .btn-toggle,.btn-danger,.btn-add,.btn-del{
    text-align: center;
  }
  .btn-toggle{
    background: green;
    font-size: 25px;
    float: right;
    padding: 0 20px;
    margin: 10px;
    color: white;
  }
  .btn-danger{
    background: red;
    font-size: 25px;
    float: right;
    padding: 0 20px;
    margin: 10px;
    color:white;
  }
  .btn-add{
    background: black;
    color:white;
  }
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
