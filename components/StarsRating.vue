<template>
  <v-rating
    :value="rating"
    :max="5"
    color="amber"
    background-color="grey lighten-2"
    readonly
    :size="18"
           
    class="custom-rating"
  ></v-rating>
</template>

<script>
export default {
  props: {
    rating: {
      type: Number,
      default: 0
    }
  }
}
</script>

<style scoped>
</style>
