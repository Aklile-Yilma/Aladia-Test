<template>
    <article>
      <p class="instructorName">{{ name }}</p>
      <p class="instructorTitle">{{ title }}</p>
      
      <section class="instructorProfile">
        <figure class="instructorImage">
          <img
            class="d-block w-100 h-90"
            :src="image"
            alt=""
          />
        </figure>
        
        <section class="profileElements">
          <ul>
            <li v-for="(icon, idx) in icons" :key="idx" class="listItem">
              <span class="listItemIcon">{{ icon }}</span>
              <span class="profileElement">{{ itemsText[idx] }}</span>
            </li>
          </ul>
        </section>
      </section>
      
      <!-- Display the faded text component -->
      <FadedText :rawHTML="description" />
    </article>
  </template>
  
  <script setup>
  import FadedText from './FadedText.vue';
  
  // Define the props that the component will receive
  const props = defineProps({
    details: {
      type: Object,
      required: true
    }
  });
  
  // Destructure the details object to extract instructor information
  const {
    display_name: name,
    job_title: title,
    image_100x100: image,
    rating,
    reviews,
    students,
    courses,
    description
  } = props.details;
  
  // Icons and text elements as reactive data
  const icons = [
    '⭐',
    '🏅',
    '👥',
    '🎥'
  ];
  const itemsText = [
    `${rating} Instructor Rating`,
    `${reviews} Reviews`,
    `${students} Students`,
    `${courses} Courses`
  ];
  </script>
  
  <style scoped>
  .instructorName {
    font-size: 1.25rem;
    font-weight: bold;
  }
  
  .instructorTitle {
    font-size: 1rem;
    color: #666;
  }
  
  .instructorProfile {
    display: flex;
    margin-top: 1rem;
  }
  
  .instructorImage {
    width: 100px;
    height: 100px;
    margin-right: 1rem;
  }
  
  .instructorImage img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 50%;
  }
  
  .profileElements {
    flex-grow: 1;
  }
  
  .listItem {
    display: flex;
    align-items: center;
    margin-bottom: 0.5rem;
  }
  
  .listItemIcon {
    margin-right: 10px;
  }
  
  .profileElement {
    font-size: 1rem;
    color: #333;
  }
  
  .d-block {
    display: block;
  }
  
  .w-100 {
    width: 100%;
  }
  
  .h-90 {
    height: 90%;
  }
  </style>
  