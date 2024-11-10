<template>
    <ul class="list">
      <!-- Loop through the links and display each item -->
      <li v-for="(link, idx) in links" :key="idx" class="item">
        <a :href="link.href" class="link">{{ link.text }}</a>
      </li>
    </ul>
  </template>
  
  <script setup>
  // Define the prop to receive links data
  defineProps({
    links: {
      type: Array,
      required: true
    }
  });
  </script>
  
  <style scoped>
.list {
    margin: 0;
    padding: 0;
    flex-grow: 1;
}

.item {
    display: flex;
    justify-content: flex-start;
    padding: 0.5rem;
}

.link {
    color: #fff;
    text-decoration: none;
}

.link:hover {
    color: #fff;
    text-decoration: underline;
}
  </style>
  