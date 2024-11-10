<template>
    <main class="mainContainer">
      <p class="sectionTitle">Instructors</p>
      <ul class="instructorList">
        <!-- Loop through the instructors array and render each instructor card -->
        <li v-for="(instructor, idx) in instructors" :key="idx" class="instructorItem">
          <InstructorCard :details="instructor" />
        </li>
      </ul>
    </main>
</template>
  
<script setup>
  // Import the InstructorCard component
  import InstructorCard from './InstructorsCard.vue';
  
  // Define props to receive details
  const props = defineProps({
    details: {
      type: Object,
      required: true
    }
  });
  
  // Extract the 'visible_instructors' array from the passed details
  const instructors = computed(() => props.details.visible_instructors);
</script>
  
<style scoped>
  .mainContainer {
    /* Styles for the main container */
  }
  
  .sectionTitle {
    font-size: 1.5rem;
    font-weight: bold;
  }
  
  .instructorList {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }
  
  .instructorItem {
    margin-bottom: 1rem;
  }
</style>
  