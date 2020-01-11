<script>
import {createEventDispatcher} from 'svelte';
const dispatch = createEventDispatcher();
let newplayer = {
   name : "",
   points : 0
 }
 const submitFunc = (e) =>{
   e.preventDefault();
   dispatch("addplayer", newplayer);
   newplayer = {
     name : "",
     points : 0
   };
 };
</script>

<form on:submit = {submitFunc}>
 <input type="text" placeholder="Player name" bind:value={newplayer.name}>
 <input type="number" placeholder="Points" bind:value={newplayer.points}>
 <input type="submit" value="Add Player" class="btn-sb">
</form>

<style>
form{
  width: 40em;
  margin: 0 auto;
}
input{
  font-size: 18px;
}
.btn-sb{
  background: teal;
  color:white;
  font-weight: bold;
  width: 10em;
  float: right;
}
@media screen and (max-width:794px){
  form{
    width: 30%;
  }
}
</style>
