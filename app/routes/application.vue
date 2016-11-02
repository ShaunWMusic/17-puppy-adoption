<template lang="html">
  <div class="app">
  <div class="nav">
    <div class="container">
      <div class="nav-left">
        <router-link to="/" class="nav-item is-brand">Puppies</router-link>
      </div>
      <div class="nav-right">
        <router-link to="/" class="nav-item">All Puppies</router-link>
        <router-link to="/new" class="nav-item">Add Puppy</router-link>
      </div>
    </div>
  </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
    };
  },

  methods: {

  },
};
</script>
