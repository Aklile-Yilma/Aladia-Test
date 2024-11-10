<template>
    <div class="relatedTopicsContainer">
        <p class="header">Explore related topics</p>
        <div class="topics">
            <span v-for="(topic, idx) in relatedTopics" :key="idx" class="topic">
                {{ topic }}
            </span>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        relatedTopics: {
            type: Array,
            default: () => ["Web Design", "Design"]
        }
    }
};
</script>

<style scoped>
.relatedTopicsContainer {
    margin: 1rem auto;
    max-width: 800px;
}

.header {
    font-size: 1.2rem;
    font-weight: 700;
    margin-bottom: 0.8rem;
}

.topics {
    display: flex;
    gap: 0.5rem;
}

.topic {
    display: inline-block;
    padding: 0.4rem 1rem;
    font-size: 1rem;
    font-weight: 600;
    color: #333;
    border: 1px solid #212020;
    border-radius: 20px;
    cursor: pointer;
    transition: background-color 0.3s, color 0.3s;
}

.topic:hover {
    background-color: #333;
    color: #fff;
}
</style>