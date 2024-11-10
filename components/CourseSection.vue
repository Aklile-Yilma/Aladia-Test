<script setup>
import { ref, watch, onMounted } from 'vue';
import { VExpansionPanels, VExpansionPanel, VExpansionPanelTitle, VExpansionPanelText } from 'vuetify/components';

const props = defineProps({
  ExpandAll: Boolean,   // Prop passed from parent to manage expansion
  sectionDetails: Object,
  idx: Number
});

const open = ref(false);

// Sync `open` with `ExpandAll` prop from parent
onMounted(() => {
  open.value = props.ExpandAll;
});

watch(() => props.ExpandAll, (newExpandAll) => {
  open.value = newExpandAll;  // Update `open` when parent changes `ExpandAll`
});

const { title, items, lecture_count: sectionLectures, content_length: sectionLength } = props.sectionDetails;
</script>

<template>
  <VExpansionPanels v-model="open">
    <VExpansionPanel>
      <VExpansionPanelTitle>
        <span class="summary-text">{{ title }}</span>
        <span class="hide">{{ sectionLectures }} lectures • {{ Math.round(sectionLength / 60) }} min</span>
      </VExpansionPanelTitle>
      <VExpansionPanelText>
        <div v-for="(item, idx) in items" :key="idx" class="lecture">
          <span :class="[(item.content_summary.includes('page') ? 'fa-regular fa-file' : 'fa-solid fa-circle-play'), 'lecture-icon']"></span>
          <span :class="[item.can_be_previewed ? 'previewed-lecture' : 'lecture-title']">
            {{ item.title }}
          </span>
          <span v-if="item.can_be_previewed" class="preview">Preview</span>
          <span class="hide">{{ item.content_summary }}</span>
        </div>
      </VExpansionPanelText>
    </VExpansionPanel>
  </VExpansionPanels>
</template>

<style scoped>
.accordion {
  box-shadow: none !important;
  width: 100%;
  border-radius: 0 !important;
}

.summary-text {
  font-weight: bold;
  flex-grow: 1;
}

.lecture {
  display: flex;
  margin: 0.7rem 0;
}

.lecture-title {
  padding-left: 1rem;
  flex-grow: 1;
}

.previewed-lecture {
  text-decoration: underline;
  color: #5624d0;
  cursor: pointer;
  flex-grow: 1;
  padding-left: 1rem;
}

.preview {
  padding: 0 0.5rem;
  text-decoration: underline;
  cursor: pointer;
  color: #5624d0;
}

.preview:hover {
  color: #4c27aa;
}

.preview,
.hide {
  display: block;
}

.lecture .hide {
  color: #6a6f73;
}

.lecture-icon {
  padding-top: 4px;
}
</style>
