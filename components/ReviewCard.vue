<template>
    <main class="mainContainer">
      <p class="userName">{{ review.user.public_display_name }}</p>
      
      <div class="rating">
        <div class="wrapper">
          <StarsRating :rating="parseInt(review.rating)" fontSize="1rem" />
        </div>
        <p class="postingTime">{{ review.created_formatted_with_time_since }}</p>
      </div>
      
      <!-- Render HTML content using v-html -->
      <div v-html="review.content_html"></div>
      
      <p class="footer">
      <!-- Vuetify's thumbs-up and thumbs-down icons -->
      <button @click="handleThumbUp" class="buttonIcon">
        <v-icon>mdi-thumb-up-outline</v-icon>
      </button>
      <button @click="handleThumbDown" class="buttonIcon">
        <v-icon>mdi-thumb-down-outline</v-icon>
      </button>
      <span class="report">Report</span>
    </p>
    </main>
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
  .mainContainer {
    padding: 1rem;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 1rem;
  }
  
  .userName {
    font-size: 1.1rem;
    font-weight: bold;
  }
  
  .rating {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 0.5rem;
  }
  
  .wrapper {
    display: flex;
  }
  
  .postingTime {
    font-size: 0.9rem;
    color: #888;
  }
  
  .footer {
    margin-top: 1rem;
    display: flex;
    align-items: center;
  }
  
  .buttonIcon {
    background: none;
    border: none;
    cursor: pointer;
    padding: 0.5rem;
    margin-right: 0.5rem;
  }
  
  .icons {
    font-size: 1.5rem;
    color: #888;
  }
  
  .report {
    color: #007bff;
    cursor: pointer;
  }
  </style>
  