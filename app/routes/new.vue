<template lang="html">
  <div class="">
    <form @submit.prevent="savePuppy">
      <label for="puppy-name">Name</label>
      <input id="puppy-name" type="text" placeholder="" v-model="formValues.name">

      <label for="puppy-age">Age</label>
      <input id="puppy-age" type="text" placeholder="" v-model="formValues.age">

      <label for="puppy-sex">Sex</label>
      <select v-model="formValues.sex">
        <option value="">Please Select an Option</option>
        <option value="Male">Male</option>
        <option value="Female">Female</option>
      </select>

      <label for="puppy-color">Color</label>
      <input id="puppy-color" type="text" placeholder="" v-model="formValues.color">

      <label for="puppy-breed">Breed</label>
      <input id="puppy-breed" type="text" placeholder="" v-model="formValues.breed">

      <label for="puppy-image-url">Image Url</label>
      <input id="puppy-image-url" type="text" placeholder="" v-model="formValues.imageurl">

      <label for="puppy-description">Description</label>
      <input id="puppy-description" type="text" placeholder="" v-model="formValues.description">

      <div class="flex flex-between">
      <router-link
      :to="{ name: 'index' }"
      class="button button-clear">
      Back
    </router-link>

      <button>Submit</button>
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
        imageurl: '',
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
