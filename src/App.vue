<script>
export default {
  data() {
    return {
      name: 'James Nyakundi',
      status: true
    }
  },
};
</script>

<template>

  <div>

    <h1>{{ name }}</h1>

    <p v-if="status">Use is Active</p>
    
  </div>

</template>
