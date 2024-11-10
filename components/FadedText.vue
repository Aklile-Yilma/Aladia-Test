<template>
    <div>
      <div :class="expanded ? 'descriptionContent' : 'descriptionContentFaded'" class="wrapper">
        <div v-html="formattedHTML"></div>
      </div>
  
      <button @click="toggleExpand" class="showMoreButton">
        Show {{ expanded ? 'less' : 'more' }}
        <span v-if="expanded">↑</span>
        <span v-else>↓</span>
      </button>
    </div>
</template>
  
  <script setup>
  import { ref, computed } from 'vue';
  
  // Props to receive raw HTML text
  const props = defineProps({
    rawHTML: {
      type: String,
      required: true
    }
  });
  
  console.log("hereeeeeeeeeeeeeeee", props.rawHTML)
  // Reactive state for expanded
  const expanded = ref(false);
  
  // Computed property for forma""tted HTML
  const formattedHTML = computed(() => {
    let text = props.rawHTML
      .replace(/<ul>/g, '<div class="pointsCollection">')
      .replace(/<\/ul>/g, '</div>')
      .replace(/<li><p>/g, '<p class="point"><i class="fa-solid fa-circle dotIcon"></i>')
      .replace(/<\/p><\/li>/g, '</p>');
  
    return text;
  });
  
  // Toggle the expansion state
  function toggleExpand() {
    expanded.value = !expanded.value;
  }
  </script>
  
  <style scoped>
.dotIcon {
    font-size: 6px;
    margin-right: 1rem;
}

.point {
    margin-left: 1rem;
    margin-bottom: 0.5rem;
}

.wrapper {
    position: relative;
}

.descriptionContentFaded {
    height: 15rem;
    overflow: hidden;
}

.descriptionContentFaded:before {
    content: '';
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    background: linear-gradient(transparent 150px, white);
}

.showMoreButton {
    font-size: 1.2rem;
    font-weight: 700;
    color: #5624d0;
    background-color: transparent;
    border: none;
}

.showMoreButton:hover {
    color: #6f42c1;
}

@media only screen and (min-width: 600px) {
    .showMoreButton {
        font-size: 1.4rem;
    }
}
  </style>
  