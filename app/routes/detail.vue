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
          <table class="table">
            <thead>
              <tr>
                <th>Age</th>
                <th>Breed</th>
                <th>Color</th>
                <th>Sex</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="puppy in puppies">
                <td>{{ puppy.age }}</td>
                <td>{{ puppy.breed }}</td>
                <td>{{ puppy.color }}</td>
                <td>{{ puppy.sex }}</td>
                <td></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>


  </div>
</template>

<script>
export default {
  props: ['apiUrl'],

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
