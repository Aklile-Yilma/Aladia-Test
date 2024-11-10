<template>
    <v-main class="main-container">
      <p class="header">Requirements</p>
      <v-list>
        <v-list-item
          v-for="(requirement, idx) in requirements"
          :key="idx"
          class="requirement"
        >
          <v-list-item-icon>
            <v-icon small>mdi-record-circle</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ requirement }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-main>
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
  }
  
  .header {
    font-size: 1.5rem;
    font-weight: bold;
  }
  
  .requirement {
    padding-left: 1rem;
  }
  
  .requirement .v-list-item-content {
    margin-left: -2rem;
  }
  .mainContainer {
    margin-top: 1rem;
}

.header {
    font-size: 25px;
    font-weight: 900;
}

.requirementsList {
    list-style: disc;
}

.requirement {

}
  </style>
  