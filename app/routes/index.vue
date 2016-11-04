<template lang="html">
  <div class="">
    <table class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Age</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="puppy in puppies">
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
