<template>
    <main class="mainContainer">
      <p class="header">Reviews</p>
      
      <!-- Display Reviews -->
      <div class="reviewsContainer">
        <template v-if="details.users_reviews.length">
          <ReviewCard
            v-for="(review, idx) in details.users_reviews"
            :key="idx"
            :review="review"
          />
        </template>
      </div>
    </main>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  import ReviewCard from './ReviewCard.vue';
  
  // Define the props for the details object
  const props = defineProps({
    details: {
      type: Object,
      required: true
    }
  });
  
  // Reactive state for search term and stars rating
  const stars = ref(0);
  
  // Method to set the stars rating (passed to child component as well)
  const setStars = (star) => {
    stars.value = star;
  };
  
//   // Filter the reviews based on search term and stars rating
//   const filteredReviews = computed(() => {
//     let reviews = props.details.users_reviews;
  
//     // Filter by stars rating
//     if (stars.value) {
//       reviews = reviews.filter(review => parseInt(review.rating) === stars.value);
//     }
  
//     // Filter by search term
//     if (searchTerm.value.length) {
//       reviews = reviews.filter(review =>
//         review.content.toLowerCase().includes(searchTerm.value.toLowerCase())
//       );
//     }
  
//     return reviews;
//   }
// );
  </script>
  
  <style scoped>
  .mainContainer {
    padding: 1rem;
  }
  
  .header {
    font-size: 1.5rem;
    font-weight: bold;
  }
  
  .reviewsContainer {
    margin-top: 1rem;
  }
  
  h2 {
    color: #777;
  }
  </style>
  