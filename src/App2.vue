<script>
export default {
  data() {
    return {
      name: 'James Nyakundi',
      status: 'active',
      users: ['James Nyakundi', 'Auka Reuben', 'Joseph Auka']
    };
  },
  methods: {
    toggleStatus() {
      if(this.status === 'active') {
        this.status = 'pending';
      }else if(this.status === 'pending') {
        this.status = 'inactive';
      } else {
        this.status = 'active';
      }
    }
  }
}
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
      <li v-for="user in users" :key="user">{{ user }}</li>
    </ul>
  
    <button v-on:click="toggleStatus">Change Status</button>
  </div>

</template>
