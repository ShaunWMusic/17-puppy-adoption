<template lang="html">
  <div class="">

    <h2 class="title">Found a Pupper? We Can Help!</h2>
    <form @submit.prevent="savePuppy">
      <div class="control">
        <label for="puppy-name">Name</label>
        <input id="puppy-name" class="input"type="text" placeholder="" v-model="formValues.name">
      </div>

      <div class="control">
        <label for="puppy-age">Age</label>
        <input id="puppy-age" type="text" class="input" placeholder="" v-model="formValues.age">
      </div>

      <div class="control">
        <label for="puppy-sex">Sex</label>
        <div class="select is-fullwidth">
          <select v-model="formValues.sex">
            <option value="">Please Select an Option</option>
            <option value="Male">Male</option>
            <option value="Female">Female</option>
          </select>
        </div>
      </div>

      <div class="control">
        <label for="puppy-color">Color</label>
        <input id="puppy-color" class="input" type="text" placeholder="" v-model="formValues.color">
      </div>

      <div class="control">
        <label for="puppy-breed">Breed</label>
        <input id="puppy-breed" class="input" type="text" placeholder="" v-model="formValues.breed">
      </div>

      <div class="control">
        <label for="puppy-image-url">Image Url</label>
        <input id="puppy-image-url" class="input" type="text" placeholder="" v-model="formValues.image_url">
      </div>

      <div class="control">
        <label for="puppy-description">Description</label>
        <input id="puppy-description" class="input" type="text" placeholder="" v-model="formValues.description">
      </div>

      <div class="control">
        <div class="flex flex-between">
        <router-link
        :to="{ name: 'index' }"
        class="button">
        Back
            </router-link>

        <button class="button is-info">Submit</button>
      </div>
      </div>
      </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formValues: {
        Name: '',
        age: '',
        sex: '',
        color: '',
        breed: '',
        image_url: '',
        description: '',
      }
    };
  },

  methods: {
    savePuppy() {
  //tell the application to save a new lunch spot
  this.$emit('addPuppy', this.formValues);

}
  },
};
</script>
