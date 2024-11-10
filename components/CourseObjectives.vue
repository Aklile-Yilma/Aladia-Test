<template>
  <div class="objectivesContainer">
    <p class="header">What you'll learn</p>
    <section class="objectives">
      <div v-for="(objective, idx) in courseDetails.objectives_summary" :key="idx" class="objective">
        <v-icon>mdi-check</v-icon>
        <i class="fa-solid fa-check check-icon"></i>
        <span>{{ objective }}</span>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  props: {
    courseDetails: Object
  }
};
</script>

<style scoped>
.objectivesContainer {
  margin: 0 auto 1rem auto;
  border: 1px solid #ddd;
  padding: 1.5rem;
  background-color: #fff;
  max-width: 800px;
}

.header {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.objectives {
  display: grid;
  grid-template-columns: 1fr 1fr;
  /* Creates two columns */
  gap: 1rem 2rem;
  /* Adds spacing between rows and columns */
}

.objective {
  display: flex;
  align-items: start;
  /* Aligns icon and text vertically */
  font-size: 1rem;
}

.check-icon {
  color: #333;
  font-size: 1.2rem;
  margin-right: 0.5rem;
}
</style>