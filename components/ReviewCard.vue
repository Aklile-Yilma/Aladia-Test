<template>
  <div class="review-card">
    <!-- User Info and Rating -->
    <div class="user-info">
      <div class="user-avatar">{{ review.user.public_display_name.charAt(0).toUpperCase() }}</div>
      <div class="user-details">
        <p class="user-name">{{ review.user.public_display_name }}</p>
        <div class="rating">
          <v-icon v-for="n in 5" :key="n" :class="{ 'filled-star': n <= parseInt(review.rating) }" class="star-icon">
            mdi-star
          </v-icon>
          <span class="posting-time">{{ review.created_formatted_with_time_since }}</span>
        </div>
      </div>
      <v-icon class="more-options-icon">mdi-dots-horizontal</v-icon>
    </div>

    <!-- Review Content -->
    <div v-html="review.content_html" class="review-text"></div>

    <!-- Footer with Helpful Icons and Report -->
    <div class="review-footer">
      <p class="helpful-text">Helpful?</p>
      <button @click="handleThumbUp" class="button-icon">
        <v-icon>mdi-thumb-up-outline</v-icon>
      </button>
      <button @click="handleThumbDown" class="button-icon">
        <v-icon>mdi-thumb-down-outline</v-icon>
      </button>
      <span class="report">Report</span>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
import StarsRating from './StarsRating.vue';

const props = defineProps({
  review: {
    type: Object,
    required: true
  }
});

// Method to handle the thumbs-up click
const handleThumbUp = () => {
  console.log('Thumb Up clicked');
};

// Method to handle the thumbs-down click
const handleThumbDown = () => {
  console.log('Thumb Down clicked');
};
</script>

<style scoped>
.review-card {
  padding: 1rem;
  background-color: #fff;
  margin-bottom: 1rem;
  border-top: 1px solid #ddd;
  border-bottom: 1px solid #ddd;
}

.user-info {
  display: flex;
  align-items: center;
  margin-bottom: 1rem;
}

.user-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #555;
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 1rem;
  margin-right: 0.75rem;
}

.user-details {
  flex-grow: 1;
}

.user-name {
  font-size: 1rem;
  font-weight: bold;
  margin: 0;
}

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


.posting-time {
  font-size: 0.8rem;
  color: #888;
  margin-left: 0.5rem;
}

.more-options-icon {
  font-size: 1.2rem;
  color: #888;
  cursor: pointer;
}

.review-text {
  font-size: 1rem;
  color: #333;
  line-height: 1.5;
  margin-bottom: 1rem;
}

.review-footer {
  display: flex;
  align-items: center;
  font-size: 0.9rem;
  color: #555;
}

.helpful-text {
  margin-right: 0.5rem;
}

.button-icon {
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.25rem;
  margin-right: 0.5rem;
  display: flex;
  align-items: center;
}

.button-icon v-icon {
  font-size: 1.2rem;
  color: #888;
}

.report {
  color: #007bff;
  cursor: pointer;
  margin-left: 1rem;
}

.report:hover {
  color: #0056b3;
}
</style>