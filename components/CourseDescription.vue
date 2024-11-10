<template>
    <div class="mainContainer">
      <p class="header">Description</p>
      <FadedText :rawHTML="details.description" />
    </div>
  </template>
  
  <script setup>
  import FadedText from './FadedText.vue';
  
  // Props to receive data from the parent component
  defineProps({
    details: {
      type: Object,
      required: true
    }
  });
  </script>
  
  <style scoped>

    .header {
    font-size: 25px;
    font-weight: 900;
}

  </style>
  