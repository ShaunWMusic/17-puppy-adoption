<template lang="html">
  <div class="">
        <h2 class="title has-text-centered">
        {{ puppy.name }}
        <button class="button is-primary" @click="adopted" v-if="puppy.adopted">
          <span class="icon">
            <i class="fa fa-paw"></i>
          </span>
            <span>I'm Adopted!</span>
        </button>
        <button class="button is-success" @click="adopted" v-else>
          <span class="icon">
            <i class="fa fa-paw"></i>
          </span>
            <span>Adopt Me!</span>
        </button>
      </h2>
      <div class="columns">
        <div class="column is-half is-offset-3">
          <div class="card">
            <div class="card-image">
              <figure class="image is-square">
                <img :src="puppy.image_url" alt="">
              </figure>
            </div>
          </div>
          <div class="column has-text-centered">
            <router-link class="button is-info" :to="{ name: 'edit', params: { id: puppy.id }}">
              <span>Update</span>
              <span class="icon">
                <span class="fa fa-pencil-square-o"></span>
              </span>
            </router-link>
            <button class="button is-danger" @click="removePuppy">
              <span>Delete</span>
              <span class="icon">
                <span class="fa fa-times"></span>
              </span>
            </button>
          </div>
        </div>
      </div>

      <nav class="level">
        <div class="level-item has-text-centered">
          <p class="heading">Age</p>
          <p class="title">{{ puppy.age }}</p>
        </div>
        <div class="level-item has-text-centered">
          <p class="heading">Breed</p>
          <p class="title">{{ puppy.breed }}</p>
        </div>
        <div class="level-item has-text-centered">
          <p class="heading">Color</p>
          <p class="title">{{ puppy.color }}</p>
        </div>
        <div class="level-item has-text-centered">
          <p class="heading">Sex</p>
          <p class="title">{{ puppy.sex }}</p>
        </div>
      </nav>
      <h2 class="title">About Me</h2>
      <p>{{puppy.description}}</p>
  </div>
</template>

<script>
export default {
  props: ['apiUrl', 'puppies'],

  data() {
    return {
      id: this.$route.params.id,
      puppy: {},
    };
  },

  mounted() {
    this.loadData()
  },

  watch: {
    // call again the method if the route changes
    '$route': 'loadData',
    'puppies': 'loadData',
  },

  methods: {
    loadData() {
      const puppy = this.puppies.find((puppy) => puppy.id === this.$route.params.id);

      if (puppy) {
        this.puppy = puppy;
      } else {
        fetch(`${this.apiUrl}/${this.$route.params.id}`)
          .then((r) => r.json())
          .then((puppy) => {
            this.puppy = puppy;
          });
      }
    },


    removePuppy() {
      if (confirm('Are you sure')) {
        this.$emit('removePuppy', this.puppy)
      }
    },

    adopted(input) {
      this.$emit('updatePuppy', this.puppy.id, { adopted: !this.puppy.adopted });
    },
  },
};
</script>
