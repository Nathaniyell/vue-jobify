<script>
export default{
  data(){
    return{
      name: "John Doe",
      status: false,
      state: "",
      todos:["come", "go", "bring", "write", "sing", "dance", "eat"],
      link: "https://nathanielessien.vercel.app",
  
    }
  },
  methods:{
    toggleState(){
    if(this.state === "online"){
      this.state = "pending"
    }else if(this.state === "pending"){
      this.state = "inactive"
    }else{
      this.state = "online"
    }
      }
  }
}

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status">User is active</p> 
  <p v-else="status">User is inactive</p>
  <!-- The above checks if the user state and displays the appropriate message based on the status boolean -->

   <p v-if="state==='online'">user is online</p>
   <p v-else-if="state==='pending'">user is pending</p>
   <p v-else>User is offline</p>


   <h3>Tasks:</h3>
   <ul>
    <li v-for="todo in todos" :key="task">{{ todo }}</li>
   </ul>

   <a target="_blank" v-bind:href="link">Visit my portfolio</a>
   <br>
   <!-- <button v-on:click="toggleState">Change state</button> -->
   <button @click="toggleState">Change state</button>
</template>

<style scoped>

h1{
  color: red; 
}
</style>
