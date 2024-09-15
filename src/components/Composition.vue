<script setup>
import { ref, onMounted } from 'vue';

const name = ref('John Doe');
const status = ref(true);
const state = ref('pending');
const todos = ref(['come', 'go', 'bring', 'write', 'sing', 'dance', 'eat']);
const newTodo = ref('');

const toggleState = () => {
    if (state.value === 'online') {
        state.value = 'pending';
    } else if (state.value === 'pending') {
        state.value = 'inactive';
    } else {
        state.value = 'online';
    }
};

const addTodo = () => {
    if (newTodo.value.trim() !== '') {
     // If the input field is not empty when the submit button is clicked, add the todo to the list of todos 
     todos.value.push(newTodo.value)

// then clear the input field
newTodo.value = ""
    }
};
      
        const removeTodo = (index)=>{
            todos.value.splice(index,1)
        }

//Fetch data from an API
   onMounted(async () => {
    try {
        // const response = await fetch('https://run.mocky.io/v3/16c30903-3570-44ea-a0e8-848cbeffc3a6');
        const response = await fetch('https://jsonplaceholder.typicode.com/todos');
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        const data = await response.json();
        todos.value = data.slice(0,20).map(todo=>todo.title);
        // console.log(todos.value);
    } catch (error) {
        console.error('There was a problem with the fetch operation:', error);
    }
});

       </script>

<template>
    <h1>{{ name }}</h1>
    <p v-if="status">User is active</p>
    <p v-else="status">User is inactive</p>
    <!-- The above checks if the user state and displays the appropriate message based on the status boolean -->

    <p v-if="state === 'online'">user is online</p>
    <p v-else-if="state === 'pending'">user is pending</p>
    <p v-else>User is offline</p>

<form @submit.prevent="addTodo">
<label for="newTodo">Add Task</label>
<input type="text" id="newTodo" name="newTodo" v-model="newTodo">
<button type="submit">Add todo</button>
</form>


    <h3>Tasks:</h3>
    <ul>
        <li v-for="(todo, index) in todos" :key="index">
            <span> {{ todo }}</span>
            <button type="button" @click="removeTodo(index)">Delete</button>
           </li>
    </ul>

    <a target="_blank" v-bind:href="link">Visit my portfolio</a>
    <br>
    <!-- <button v-on:click="toggleState">Change state</button> -->
    <button @click="toggleState">Change state</button>
</template>

<style scoped>
h1 {
    color: red;
}
</style>
