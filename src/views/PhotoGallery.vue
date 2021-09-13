<template>
  <div class="d-flex flex-wrap">
    <b-img
      v-for="picture in images"
      :key="picture.id"
      :src="`http://localhost:1337${picture.url}`"
      class="m-2 w-25"
    />
  </div>
</template>

<script>
  import axios from 'axios';
  export default {
    name: "PhotoGallery",

    data(){
      return {
        carts: []
      }
    },

    computed: {
      images() {
        return this.carts.flatMap(cart => cart.Pictures)
      }
    },

    mounted(){
      axios.get(
        'http://localhost:1337/carts'
      )
        .then(res => {
          this.carts = res.data
        })
    }
  }
</script>

<style scoped>
.gallery{
  background-color: red;
}
</style>
