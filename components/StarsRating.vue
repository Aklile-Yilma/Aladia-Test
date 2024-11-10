<template>
  <v-icon v-for="n in 5" :key="n" :class="{ 'filled-star': n <= parseInt(rating) }" class="star-icon">
    mdi-star
  </v-icon>
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
.rating {
  display: flex;
  align-items: center;
  margin-top: 0.25rem;
}


.star-icon {
  color: #ccc;
  font-size: 1rem;
  margin-right: 2px;
}

.filled-star {
  color: #b4690e;
  /* Color for filled stars */
}
</style>
