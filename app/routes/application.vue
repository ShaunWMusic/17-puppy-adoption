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

    <div class="main section">
      <div class="container">
        <div class="columns">
          <div class="column is-4">
            <div class="panel">
              <p class="panel-heading">Adopt a Pupper</p>
              <div class="panel-block is-active" v-for="puppy in puppies">
                <div class="media">
                   <div class="media-left">
                       <figure class="image is-64x64">
                         <img :src="puppy.image_url" alt="">
                       </figure>
                    </div>
                    <div class="">
                       <h2 class="subtitle">{{ puppy.name }}</h2>
                      <router-link class="is-primary" :to="{ name: 'detail', params: { id: puppy.id } }">
                      read more
                    </router-link>
                   </div>
                 </div>
              </div>
            </div>
          </div>
          <div class="column">
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
    </div>
  </div>
</template>

<script>
import IndexPage from './index.vue';
const apiUrl = 'https://tiy-tn-class-api-fall-16.herokuapp.com/puppies/shaun';

export default {
  componenets: {
    IndexPage,
  },
  data() {
    return {
      apiUrl,
      puppies: [],
      path: window.location.pathname,
    };
  },

  mounted() {
    this.getpuppies();
  },

  methods: {
    getpuppies() {
    fetch(apiUrl)
    .then((r) => r.json())
    .then((puppies) => {
      this.puppies = puppies;
    });
  },

    addPuppy(input) {
      fetch(apiUrl, {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify(input),
      })
      .then((r) => r.json())
      .then((puppies) => {
        this.puppies = [puppies, ...this.puppies]

        this.$router.push({ name: 'index' })
      })
      console.log('add', input);
    },

    removePuppy(puppies) {
      fetch(`${apiUrl}/${puppies.id}`, {
        method: 'DELETE',
      })
      .then(() => {
        this.puppies = this.puppies.filter((old) => old.id !== puppies.id);

        this.$router.push({ name: 'index' });
      });
    },

    updatePuppy() {}
  },
};
</script>
