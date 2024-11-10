<template>
  <div class="content-container">
    <!-- New Course Includes Section -->
    <div class="course-includes">
      <p class="includes-header">This course includes:</p>
      <div class="features">
        <div v-for="(feature, idx) in courseIncludes" :key="idx" class="feature">
          <v-icon>{{ feature.icon }}</v-icon>
          <i :class="feature.icon" class="feature-icon"></i>
          <span>{{ feature.text }}</span>
        </div>
      </div>
    </div>

    <p class="header">Course content</p>
    <section class="before-content">
      <p>{{ sections.length }} sections • {{ numOfLectures }} lectures • {{ timeInHours }}h {{ remainingMinutes }}m
        total length</p>
      <button @click="handleClick" class="expand-all-button">
        {{ open ? 'Collapse' : 'Expand' }} all sections
      </button>
    </section>

    <VList class="list">
      <VListItem v-for="(section, idx) in sections" :key="idx" class="list-item">
        <CourseSection :ExpandAll="open" :sectionDetails="section" :idx="idx" />
      </VListItem>
    </VList>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import CourseSection from './CourseSection.vue';
import { VList, VListItem } from 'vuetify/components';

const props = defineProps({
  details: Object
});

const open = ref(false); // Manage overall expansion state
const handleClick = () => {
  open.value = !open.value;
};

const content = computed(() => props.details?.curriculum_context);
const sections = computed(() => content.value?.data?.sections || []);
const numOfLectures = computed(() => content.value?.data?.num_of_published_lectures || 0);
const timeInSeconds = computed(() => content.value?.data?.estimated_content_length_in_seconds || 0);

const timeInHours = computed(() => Math.floor(timeInSeconds.value / 3600));
const remainingMinutes = computed(() => Math.round((timeInSeconds.value % 3600) / 60));

// Data for course includes section
const courseIncludes = [
  { icon: "mdi-youtube-tv", text: "21.5 hours on-demand video" },
  { icon: "mdi-folder-download-outline", text: "9 downloadable resources" },
  { icon: "mdi-calendar-text-outline", text: "Assignments" },
  { icon: "mdi-cellphone", text: "Access on mobile and TV" },
  { icon: "mdi-file-document-outline", text: "23 articles" },
  { icon: "mdi-glass-flute", text: "Certificate of completion" }
];
</script>

<style scoped>
.contentContainer {
  margin: 0 auto;
  padding: 1rem 0;
}

.header {
  margin-top: 1rem;
  font-size: 1.2rem;
  font-weight: 900;
}

.beforeContent {
  display: flex;
  flex-wrap: wrap;
}

.beforeContent p {
  margin: 0;
  flex-grow: 2;
  min-width: 75%;
}

.expandAllButton {
  color: #5624d0;
  border: none;
  background-color: transparent;
  font-weight: 700;
  font-size: 1.1rem;
}

.expandAllButton:hover {
  color: #4c27aa;
}

.list {
  border: 1px solid lightgray;
}

.listItem {
  border: 1px solid lightgray;
  padding: 0;
}

/* New styles for "This course includes" section */
.course-includes {
  margin-top: 0.6rem;
  margin-bottom: 1.2rem;
}

.includes-header {
  font-size: 1.2rem;
  font-weight: 700;
  margin-bottom: 0.6rem;
}

.features {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.feature {
  display: flex;
  align-items: center;
  font-size: 1rem;
}

.feature-icon {
  margin-right: 0.5rem;
  color: #333;
  font-size: 1.2rem;
}

.showMoreButton {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #1c1d1f;
  background-color: #fff;
  font-weight: bold;
  margin-top: 1rem;
}

.showMoreButton:hover {
  background-color: whitesmoke;
}

.hide {
  display: none;
}

.before-content {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
  margin-top: 0.5rem;
}

.expand-all-button {
  color: #5022c3;
  font-weight: 600;
}
</style>