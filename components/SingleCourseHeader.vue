<template>
    <main :class="['mainContainer']">
      <div class="body">
        <section class="categoriesSection">
          <router-link to="/">
            <p class="subCategory">Design ></p>
          </router-link>
          <i class="fa-solid fa-chevron-right sub-category-arrow"></i>
          <router-link to="/">
            <p class="subCategory">Web Design ></p>
          </router-link>
          <router-link to="/">
            <p class="subCategory">Web Design</p>
          </router-link>
        </section>
        <section class="coursePreview">
          <figure :class="['imageWrapper', 'hide']">
            <img :src="image" :alt="courseDetails.category" />
          </figure>
          <section class="mainDetails">
            <h1 class="title">{{ title }}</h1>
            <p>{{ headline }}</p>
            <p class="rating">{{ rating.toPrecision(2) }}</p>
  
            <StarsRating :rating="rating" />
            <p class="linkLikeText">(19,080 ratings)</p>
            <p style="display: inline-block; margin-left: 7px;">
              {{ subscribers }} students
            </p>
            <p>
              Created by
              <span class="linkLikeText">
                {{ instructors?.map(instructor => instructor.name).join(', ') }}
              </span>
            </p>
            <div class="lastUpdateLangWrapper">
              <p>
                <i class="fa-solid fa-circle-exclamation"></i>
                <span class="lastUpdate">
                  Last updated
                  <span class="lastUpdateDate">
                    {{ formattedDate }}
                  </span>
                </span>
              </p>
              <p>
                <i class="fa-solid fa-globe"></i> English
              </p>
              <p>
                <i class="fa-solid fa-closed-captioning"></i>
                <span class="languages">
                  {{ languages.join(', ') }}
                </span>
              </p>
            </div>
            <div class="hide">
              <section class="priceAndOffer">
                <p class="headerPrice">
                  <span class="bigPrice">E£199.99</span>
                  <span class="smallPrice">E£679.99</span>
                  <span class="offerSize">71% off</span>
                </p>
                <p class="timeRemaining">
                  <i class="fa-regular fa-clock"></i>
                  <span class="offerText">
                    <span class="bold">5 hours</span> left at this price!
                  </span>
                </p>
              </section>
              <footer class="previewFooter">
                <button type="button" class="addToCartButton">Add to cart</button>
                <p class="text-center p-3 pb-0">30-Day Money-Back Guarantee</p>
                <p class="text-center">Full Lifetime Access</p>
                <div class="previewFooterButtons">
                  <button class="footerButton">Share</button>
                  <button class="footerButton">Gift this course</button>
                  <button class="footerButton">Apply Coupon</button>
                </div>
              </footer>
            </div>
          </section>
        </section>
      </div>
    </main>
  </template>
  
  <script>
  import { computed } from 'vue';
  import StarsRating from './StarsRating.vue';
  
  export default {
    components: {
      StarsRating
    },
    props: {
      courseDetails: Object,
      additionalDetails: Object
    },
    setup(props) {
      const { title, image_750x422: image, headline, rating, num_subscribers: subscribers, visible_instructors: instructors, last_update_date: lastUpdate, caption_languages: languages } = props.courseDetails;
      const [year, month] = lastUpdate.split('-');
      const date = new Date(year, month - 1);
  
      const formattedDate = computed(() => `${date.getMonth() + 1}/${date.getFullYear()}`);
  
      return {
        title,
        image,
        headline,
        rating,
        subscribers,
        instructors,
        languages,
        formattedDate
      };
    }
  };
  </script>
  
  <style scoped>
  /* Add your styles here */
.mainContainer {
    background-color: #1c1d1f;
}

.body {
    max-width: 45rem;
    margin: 0 auto;
}

.title {
    font-weight: 700;
}

.categoriesSection {
    padding: 1rem;
    font-size: 0.8em;
}

.subCategory {
    display: inline-block;
    margin: 0 6px;
    font-weight: bold;
    color: #cec0fc;
}

.sub-category-icon {
    color: #cec0fc;
}

.mainDetails {
    padding: 1rem;
    background-color: #1c1d1f;
    color: #fff;
}

.linkLikeText {
    display: inline-block;
    margin-left: 7px;
    text-decoration: underline;
    color: #cec0fc;
    cursor: pointer;
}

.lastUpdate,
.lastUpdateDate {
    margin-left: 5px;
}

.languages {
    margin-left: 5px;
}

.headerPrice {
    display: flex;
    align-items: center;
}

.bigPrice {
    font-weight: 900;
    font-size: 35px;
}

.smallPrice {
    margin-left: 5px;
    text-decoration: line-through;
}

.rating {
    display: inline;
    font-weight: bold;
    color: #f3ca8c;
    font-size: 1rem;
    margin-right: 0.5rem;
}


.offerSize {
    margin-left: 5px;
}

.bold {
    font-weight: bold;
}

.offerText {
    margin-left: 5px;
}

.timeRemaining {
    color: #b32d0f;
}

.previewFooter {
    display: flex;
    flex-direction: column;
}

.addToCartButton {
    border: none;
    background-color: #a435f0;
    color: #fff;
    cursor: pointer;
    padding: 1rem;
    font-weight: bold;
}

.previewFooterButtons {
    display: flex;
    justify-content: space-between;
}

.footerButton {
    border: none;
    background-color: transparent;
    color: #fff;
    font-weight: bold;
    border-bottom: 1px solid #fff;
    margin: 0 2rem;
    cursor: pointer;
    max-width: fit-content;
}

@media only screen and (min-width: 600px) {
    .categoriesSection {
        padding: 1rem 0;
    }
}

@media only screen and (min-width: 1080px) {
    .title {
        font-size: 2rem;
    }

    .lastUpdateLangWrapper {
        display: flex;
        flex-direction: row;
    }

    .lastUpdateLangWrapper p {
        margin: 0 0.5rem
    }

    .lastUpdateLangWrapper p:first-child {
        margin-left: 0;
    }

    .hide {
        display: none;
    }

    .categoriesSection {
        padding-left: 0.5rem;
    }

    .body {
        margin: 0 auto 0 10%;
    }
}
  </style>
  