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
      <div class="section columns">
        <div class="column is-4">
          <div class="panel">
            <p class="panel-heading">Adopt a Pupper</p>
            <div class="panel-block is-active">
              <div class="media">
                 <div class="media-left">
                     <figure class="image is-64x64">
                       <img src="http://cdn3-www.dogtime.com/assets/uploads/gallery/30-impossibly-cute-puppies/impossibly-cute-puppy-21.jpg" alt="">
                     </figure>
                  </div>
                  <div class="">
                     <h2 class="subtitle">Luna</h2>
                    <router-link to="{ name: 'detail', params: { id: item.id } }"
                    class="">
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
</template>

<script>
import IndexPage from './index.vue';
const apiUrl = 'https://tiy-tn-class-api-fall-16.herokuapp.com/puppies/shaun';


export default {
  data() {
    return {
    };
  },

  methods: {

  },
};
</script>
