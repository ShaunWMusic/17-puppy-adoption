<template lang="html">
  <div class="">
    <table class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Age</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in lunchSpots">
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>
            <router-link :to="{ name: 'detail', params: { id: item.id } }">
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
  data() {
    return {};
  },

  methods: {

  },
};
</script>
