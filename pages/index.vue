<template>
  <main>
    <section>
      <Header />
      <StickyCardContent
        v-if="fetched"
        :courseDetails="courseDetails"
        :additionalDetails="additionalDetails"
      />
      <SingleCourseHeader
        v-if="fetched"
        :courseDetails="courseDetails"
        :additionalDetails="additionalDetails"
      />
      <div v-if="fetched" class="body">
        <CourseObjectives :courseDetails="courseDetails" />
        <div class="includesSection">
          <ThisCourseIncludes :details="additionalDetails" />
        </div>
        <CourseContent :details="additionalDetails" />
        <CourseRequirements :details="additionalDetails" /> 
        <CourseDescription :details="additionalDetails" />
        <InstructorsSection :details="additionalDetails" />
        <div id="boundary">
          <ReviewsSection :details="additionalDetails" />
        </div>  
      </div>
      <Bottom />
    </section>
  </main>
</template>

<script setup>
import { ref, onMounted } from 'vue';
// Import child components
import StickyCardContent from '~/components/StickyCardContent.vue';
import SingleCourseHeader from '~/components/SingleCourseHeader.vue';
import CourseObjectives from '~/components/CourseObjectives.vue';
import ThisCourseIncludes from '~/components/ThisCourseIncludes.vue';
import CourseContent from '~/components/CourseContent.vue';
import CourseRequirements from '~/components/CourseRequirements.vue';
import InstructorsSection from '~/components/InstructorsSection.vue';
import CourseDescription from '~/components/CourseDescription.vue';
import ReviewsSection from '~/components/ReviewSection.vue';
import Header from '~/layout/Header.vue';
import Bottom from '~/layout/Bottom.vue';
import details from '~/small-data.json';
import additionalData from '~/additionalDetails.json';

// Define reactive variables to hold the course and additional data
const courseDetails = ref(null);
const additionalDetails = ref(null);
const fetched = ref(false);

onMounted(() => {
  // Populate the courseDetails and additionalDetails data
  courseDetails.value = details;
  additionalDetails.value = additionalData;

  // Set fetched flag to true when data is ready
  fetched.value = true;
});
</script>

<style scoped>
.body {
    max-width: 45rem;
    margin: 2rem auto 0 auto;
    padding: 0 0.5rem;
}

@media only screen and (min-width: 1080px) {
    .includesSection {
        display: none;
    }

    .body {
        margin: 2rem auto 0 10%;
    }
}
</style>
