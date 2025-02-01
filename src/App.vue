<script setup>
import { ref, onMounted } from 'vue';


const name = ref('James Nyakundi');
const status = ref('active');
const users = ref(['James Nyakundi', 'Auka Reuben', 'Joseph Auka']);
const newName = ref('');


const toggleStatus = () => {
  if (status.value === 'active') {
    status.value = 'pending';
  } else if (status.value === 'pending') {
    status.value = 'inactive';
  } else {
    status.value = 'active';
  }
};

const addName = () => {
  if (newName.value !== '') {
    users.value.push(newName.value);
    newName.value = '';
  }
};

const deleteName = (index) => {
  users.value.splice(index, 1);
};

onMounted(async () => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users');
    const data = await response.json();
    users.value = data.map((user) => user.name);
  } catch (error) {
    console.error(error);
    
  }
});
</script>

<template>

  <div>

    <h1>{{ name }}</h1>

    <p v-if="status === 'active'">
      User is Active
    </p>
    <p v-else-if="status == 'pending'">
      User is pending
    </p>
    <p v-else>
      User is inactive
    </p>

    <h3>Users</h3>

    <ul>
      <li v-for="(user, index ) in users" :key="user">
        <span>
          {{ user }}
        </span>

        <button @click="deleteName(index)">x</button>
      </li>
    </ul>

    <div>
      <form @submit.prevent="addName">
        <label for="newName">Add New Name</label>
        <input type="text" id="newName" name="newName" v-model="newName" />
        <button type="submit">Add User</button>
      </form>
    </div>


    <button v-on:click="toggleStatus">Change Status</button>
  </div>

</template>
