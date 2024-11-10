<template>
    <div class="content-container">
        <!-- "Show More Sections" Button -->
        <button class="show-more-sections">
            19 more sections
        </button>
    </div>
</template>

<script setup>

const props = defineProps({
    details: Object
});


</script>

<style scoped>
/* Styles for "Show More Sections" button */
.show-more-sections {
    width: 100%;
    padding: 0.6rem;
    font-size: 0.9rem;
    font-weight: 600;
    color: #333;
    border: 1px solid #333;
    background-color: transparent;
    text-align: center;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s;
    margin-top: 1rem;
}

.show-more-sections:hover {
    background-color: #f8f8f8;
}
</style>