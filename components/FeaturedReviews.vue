<template>
    <div class="review-container">
        <p class="header">Featured review</p>
        <div class="review-content">
            <v-img src="https://www.udemy.com/staticx/udemy/images/v7/logo-udemy.svg" alt="Udemy Logo" class="udemylogo"
                contain />
            <div class="user-info">
                <p class="user-name">Jochen B.</p>
                <p class="user-courses">12 courses</p>
                <p class="user-reviews">3 reviews</p>
            </div>
        </div>
        <div class="rating">
            <v-icon small class="star-icon">mdi-star</v-icon>
            <v-icon small class="star-icon">mdi-star</v-icon>
            <v-icon small class="star-icon">mdi-star</v-icon>
            <v-icon small class="star-icon">mdi-star</v-icon>
            <v-icon small class="star-icon">mdi-star</v-icon>
            <span class="review-time">4 years ago</span>
        </div>
        <p class="review-text">
            Wow, what can I say. This is for sure the best investment I've ever made. Vako is an outstanding teacher and
            the course is just amazing. It delivers great information in a super entertaining way. I'm going to come
            back again and again as there's so much that's worth to be done more than just once. If you want to learn
            Figma, Webflow and a great deal about good design in general, do yourself a favor and click the buy button.
            Thank you Vako!
        </p>
        <div class="review-actions">
            <p>Was this review helpful?</p>
            <div class="review-action-icons">
                <v-icon class="icon-button">mdi-thumb-up-outline</v-icon>
                <v-icon class="icon-button">mdi-thumb-down-outline</v-icon>
                <a href="#" class="report-link">Report</a>
            </div>
        </div>
    </div>
</template>

<script setup>
</script>

<style scoped>
.review-container {
    border: 1px solid #ddd;
    padding: 1.5rem;
    background-color: #fff;
    max-width: 800px;
    margin: 1rem auto;
    border-radius: 8px;
}

.header {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 1rem;
}

.review-content {
    display: flex;
    align-items: center;
    margin-bottom: 1rem;
}


.udemylogo {
    max-width: 60px;
    height: 60px;
    width: 60px;
    border: 1px solid rgba(0, 0, 0, 0.085);
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 1rem;
}

.user-info {
    flex-grow: 1;
}

.user-name {
    font-weight: 700;
    margin: 0;
}

.user-courses,
.user-reviews {
    font-size: 0.9rem;
    color: #555;
    margin: 0;
}

.rating {
    display: flex;
    align-items: center;
    margin: 0.5rem 0;
}

.star-icon {
    color: #b4690e;
    margin-right: 0.2px;
    font-size: 1.1rem;

}

.review-time {
    font-size: 0.7rem;
    color: #888;
    margin-left: 0.5rem;
}

.review-text {
    font-size: 0.8rem;
    color: #333;
    margin-bottom: 1rem;
}

.review-actions {
    display: flex;
    align-items: start;
    font-size: 0.9rem;
    color: #555;
    flex-direction: column;
}

.icon-button {
    font-size: 1.2rem;
    color: #333;
    cursor: pointer;
    margin: 0 0.5rem;
    background-color: transparent;
    border: 1px solid #1c1d1f;
    padding: 1rem;
    margin: 0.3rem;
    border-radius: 50%;
}

.icon-button:hover {
    color: #000;
}

.report-link {
    color: #5624d0;
    text-decoration: underline;
    margin-left: 1rem;
    cursor: pointer;
}

.report-link:hover {
    color: #4c27aa;
}
</style>