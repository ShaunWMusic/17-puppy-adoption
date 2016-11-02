<template lang="html">
  <div class="">
    <div class="section columns is-multiline">
      <div class="panel column is-one-quarter is-paddingless">
        <p class="panel-heading">Adopt a Pupper</p>
        <div class="panel-block is-active">
          <div class="media">
             <div class="media-left">
                 <img class="image is-64x64" src="http://cdn3-www.dogtime.com/assets/uploads/gallery/30-impossibly-cute-puppies/impossibly-cute-puppy-21.jpg" alt="">
              </div>
              <div class="">
                 <h2 class="">Luna</h2>
                <router-link to="{ name: 'detail', params: { id: item.id } }"
                class="">
                read more
              </router-link>
             </div>
           </div>
        </div>

      </div>
    </div>
    <div class="section columns">
      <table class="column is-half">
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
