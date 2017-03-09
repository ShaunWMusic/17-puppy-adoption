<template lang="html">
  <div class="">
    <h2 class="title">Puppies for Adoption</h2>
    <router-link to="/new" class="is-pulled-right is-info button">Add a Pupper</router-link>
    <table class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Age</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-if="!puppy.adopted" v-for="puppy in puppies">
          <td>{{ puppy.name }}</td>
          <td>{{ puppy.age }}</td>
          <td>
            <router-link class="is-primary":to="{ name: 'detail', params: { id: puppy.id } }">
              MORE!!!
            </router-link>
          </td>
        </tr>
      </tbody>
    </table>
    <h2 class="title">Adopted Puppers</h2>
    <table class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Age</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-if="puppy.adopted" v-for="puppy in puppies">
          <td>{{ puppy.name }}</td>
          <td>{{ puppy.age }}</td>
          <td>
            <router-link class="is-primary":to="{ name: 'detail', params: { id: puppy.id } }">
              MORE!!!
            </router-link>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: ['puppies'],

  data() {
    return {};
  },

  methods: {

  },
};
</script>
