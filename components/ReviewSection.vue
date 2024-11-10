<template>
  <main class="mainContainer">
    <div class="courseRating">
      <v-icon class="rating-icon">mdi-star</v-icon>
      <span class="course-rating-text">4.8 course rating • 19K ratings</span>
    </div>

    <p class="header">Reviews</p>

    <!-- Display Reviews in a Grid -->
    <div class="reviewsContainer">
      <template v-if="details.users_reviews.length">
        <div class="reviewGrid">
          <ReviewCard v-for="(review, idx) in displayedReviews" :key="idx" :review="review" />
        </div>
      </template>
    </div>

    <!-- Show all / Show less button -->
    <button v-if="details.users_reviews.length > 4" @click="toggleShowAll" class="toggleButton">
      {{ showAll ? 'Show less' : 'Show all reviews' }}
    </button>
  </main>
</template>

<script setup>
import { ref, computed } from 'vue';
import ReviewCard from './ReviewCard.vue';
import { VIcon } from 'vuetify/components';

// Define the props for the details object
const props = defineProps({
  details: {
    type: Object,
    required: true
  }
});

const showAll = ref(false); // State to control visibility of additional reviews

// Computed property to conditionally show the first 4 reviews or all reviews
const displayedReviews = computed(() => {
  return showAll.value ? props.details.users_reviews : props.details.users_reviews.slice(0, 4);
});

// Toggle function to switch between showing all reviews and only the first 4
const toggleShowAll = () => {
  showAll.value = !showAll.value;
};
</script>

<style scoped>
.mainContainer {
  padding: 1rem;
  max-width: 800px;
  margin: auto;
}

.courseRating {
  display: flex;
  align-items: center;
  font-size: 1.25rem;
  font-weight: bold;
  color: #333;
  margin-bottom: 1rem;
}

.rating-icon {
  color: #b4690e;
  margin-right: 0.5rem;
  font-size: 1.5rem;
}

.course-rating-text {
  color: #333;
}

.header {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

.reviewsContainer {
  margin-top: 1rem;
}

.reviewGrid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
}

.toggleButton {
  display: block;
  width: 20%;
  padding: 0.5rem 0.3rem;
  font-size: 0.7rem;
  font-weight: bold;
  color: #333;
  border: 1px solid #333;
  background-color: transparent;
  text-align: center;
  cursor: pointer;
  margin-top: 1.5rem;
  transition: background-color 0.3s, color 0.3s;
}

.toggleButton:hover {
  background-color: #f8f8f8;
}
</style>