<script>
  import FilterUser from "./FilterUser.svelte";
  import { debug, each } from "svelte/internal";
  import image1 from "../assets/images/image1.jpg";
  import image2 from "../assets/images/image1.jpg";
  import User from "./User.svelte";
  import NewUser from "./NewUser.svelte";
  import App from "../App.svelte";
  let users = [
    {
      id: 1,
      image: "https://cdn-icons-png.flaticon.com/128/3135/3135715.png",
      name: "Khairo",
      email: "k_mansouri@esi.dz",
      active: true,
    },
    {
      id: 2,
      image: image2,
      name: "Mohamed",
      email: "kmansouri@gmail.com",
      active: false,
    },
    {
      id: 3,
      image: image1,
      name: "MOI",
      email: "kmansouri@gmail.com",
      active: false,
    },
  ];
  $: filteredUsers = [...users];
  const getUsers = () => filteredUsers;
  const filter = (statusString) => {
  
    const status =
    statusString.detail === "true"
        ? true
        : statusString.detail === "false"
        ? false
        : null;  
    
  };
  let filterValue = null;


  const  removeUser=({detail})=>  {
    users=users.filter(u=>!(u.id===detail))
    filteredUsers=filteredUsers.filter(u=>!(u.id===detail))
  }


  const add=({detail})=>
  {
    debugger;
    users.push({id:users.length+1,image:image1,...detail})
    users=users;
    debugger;
  }
  
</script>

<div>
  <h1 class="text-2xl text-center mt-10">List of Users</h1>
  <div class="flex justify-between mx-4 items-center">
  <FilterUser on:filter={filter} />
  <NewUser on:newUser={add}/>
  </div>
  {#each filteredUsers as user, i (user.id)}
    <User {user} {i} on:remove={removeUser} />
  {:else}
    <p>No user found !</p>
  {/each}
</div>
