<script>
  import { createEventDispatcher } from "svelte";

    export let user
    export let i;
    const dispatch = createEventDispatcher();
    const remove =()=>{
      dispatch("remove",user.id)
    }
</script>
<div class="flex mt-5 bg-white border p-2 rounded-lg shadow-md
hover:shadow-lg cursor-pointer items-center relative
">
<button 
on:click={remove}
class="absolute right-0 top-0 -mt-5 rounded-full w-10 h-10 bg-red-300 hover:bg-red-600 text-white text-sm text-center">x</button>
  <p class="mx-10">{i + 1}</p>
  <img class="rounded-full w-16 h-14" src={user.image} alt={user.name} />
  <p class="mx-4 w-40">{name}</p>
  <p class="mx-4 w-40">{user.email}</p>
</div>