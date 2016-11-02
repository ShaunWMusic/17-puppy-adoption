<template lang="html">
  <div class="">
  <div class="nav">
      <div class="nav-left">
        <router-link to="/" class="nav-item is-brand">Puppies</router-link>
      </div>
      <div class="nav-right">
        <router-link to="/" class="nav-item">All Puppies</router-link>
        <router-link to="/new" class="nav-item">Add Puppy</router-link>
      </div>
  </div>

  <div class="main">
        <div class="container">
        <router-view
        :puppies="puppies"
        :api-url="apiUrl"
        @addPuppy="addPuppy"
        @removePuppy="removePuppy"
        @updatePuppy="updatePuppy">
      </router-view>
        </div>
      </div>
  </div>
</template>

<script>
import IndexPage from './index.vue';
const apiUrl = 'https://tiy-tn-class-api-fall-16.herokuapp.com/puppies/shaun';


export default {
  components: {
    IndexPage,
  },
  data() {
    return {
    };
  },

  methods: {

  },
};
</script>
