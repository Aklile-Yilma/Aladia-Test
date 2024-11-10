<template>
  <div class="main-container">
    <p class="header">Requirements</p>
    <ul class="requirements-list">
      <li v-for="(requirement, idx) in requirements" :key="idx" class="requirement">
        {{ requirement }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
  details: {
    type: Object,
    required: true,
  },
});

const requirements = props.details.prerequisites.items || [];
</script>

<style scoped>
.main-container {
  padding: 16px;
  margin-top: 1rem;
}

.header {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.requirements-list {
  list-style-type: disc;
  padding-left: 1.5rem;
  margin: 0;
}

.requirement {
  font-size: 1rem;
  color: #333;
  margin-bottom: 0.5rem;
}
</style>