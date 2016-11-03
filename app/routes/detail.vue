<template lang="html">
  <div class="">
        <h2 class="title has-text-centered">
        {{ puppy.name }}
        <button class="button is-success">
          <span class="icon">
            <i class="fa fa-paw"></i>
          </span>
          <span>I'm Adopted!</span>
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
            <button class="button is-danger" @click="removePuppy">
              <span>Delete</span>
              <span class="icon">
                <span class="fa fa-times"></span>
              </span>
            </button>
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

        </div>
      </div>


  </div>
</template>

<script>
export default {
  props: ['apiUrl'],
  props: ['puppies'],

  data() {
    return {
      id: this.$route.params.id,
      puppy: {},
    };
  },

  mounted() {
    this.loadData()
  },

  methods: {
    loadData() {
      fetch(`${this.apiUrl}/${this.id}`)
        .then((r) => r.json())
        .then((puppy) => {
          this.puppy = puppy;
        })
        // .catch(() => {
        //   this.$router.push({ name: 'index' });
        // });
    },

    removePuppy() {
      if (confirm('Are you sure')) {
        this.$emit('removePuppy', this.puppy)
      }
    }
  },
};
</script>
