<template>
  <main :class="['mainContainer']" :style="{
    position: 'absolute',
    marginTop: hidden ? '1rem' : '2rem',
    boxShadow: hidden ? '0 10px 10px #c2c9d6' : '0 5px 5px #c2c9d6'
  }">
    <figure :class="hidden ? 'hide' : 'imageWrapper'">
      <img class="d-block w-100" :src="image" alt="Course preview image" />
      <figcaption class="previewButton">Preview this course</figcaption>
    </figure>

    <div class="tab-menu">
      <span :class="{ active: selectedTab === 'personal' }" @click="selectedTab = 'personal'">Personal</span>
      <span :class="{ active: selectedTab === 'teams' }" @click="selectedTab = 'teams'">Teams</span>
    </div>

    <div v-if="selectedTab === 'personal'" class="cardBody">
      <h2>Subscribe to Udemy’s top courses</h2>
      <p>Get this course, plus 12,000+ of our top-rated courses, with Personal Plan.
        <a href="#" class="learn-more">Learn more</a>
      </p>

      <button class="btn-primary">Try Personal Plan for free</button>
      <p style="display: flex; text-align:center; align-items: center; color: #aaa; font-size: 0.8rem;">
        Starting at $10.00 per month after trial<br />Cancel anytime
      </p>

      <div class="separator">
        <span>or</span>
      </div>

      <p class="price">$74.99</p>
      <button class="addToCartButton button">Add to cart</button>
      <p class="text-center">30 Day Money Back Guarantee<br />Full Lifetime Access</p>

      <section class="buttonsWrapper">
        <button class="footerButton">Share</button>
        <button class="footerButton">Gift this course</button>
        <button class="footerButton">Apply Coupon</button>
      </section>

      <div class="coupon-section" v-if="isCouponApplied">
        <p><span class="coupon-section-title"> {{ couponCode }}</span> is applied Udemy coupon</p>
        <button @click="removeCoupon" class="remove-coupon">✕</button>
      </div>

      <div class="coupon-input">
        <input v-model="inputCoupon" placeholder="Enter Coupon" />
        <button @click="applyCoupon">Apply</button>
      </div>
    </div>

    <div v-if="selectedTab === 'teams'" class="businessCard">
      <img src="./assets/logo-udemy.png" alt="Udemy Business" class="udemyBusinessLogo" />
      <!-- replace with the actual logo path -->
      <p>Subscribe to this course and 27,000+ top-rated Udemy courses for your organization.</p>
      <button class="btn-primary">Try Udemy Business</button>
      <ul class="benefits">
        <li>✔ For teams of 2 or more users</li>
        <li>✔ 27,000+ fresh & in-demand courses</li>
        <li>✔ Learning Engagement tools</li>
        <li>✔ SSO and LMS Integrations</li>
      </ul>
    </div>
  </main>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from 'vue';

export default {
  props: {
    courseDetails: Object
  },
  setup(props) {
    const hidden = ref(false);
    const selectedTab = ref('personal');
    const image = props.courseDetails.image_750x422;
    const inputCoupon = ref('');
    const couponCode = ref('LETSLEARNNOW');
    const isCouponApplied = ref(true);

    const handleStyles = () => {
      if (window.scrollY > 400) {
        hidden.value = true;
      } else {
        hidden.value = false;
      }
    };

    const applyCoupon = () => {
      isCouponApplied.value = true;
      couponCode.value = inputCoupon.value;
    };

    const removeCoupon = () => {
      isCouponApplied.value = false;
      inputCoupon.value = '';
    };

    onMounted(() => {
      window.addEventListener('scroll', handleStyles);
    });

    onBeforeUnmount(() => {
      window.removeEventListener('scroll', handleStyles);
    });

    return {
      hidden,
      selectedTab,
      image,
      inputCoupon,
      couponCode,
      isCouponApplied,
      applyCoupon,
      removeCoupon
    };
  }
};
</script>

<style scoped>
.mainContainer {
  display: none;
  margin-left: 65rem;
  width: 20rem;
  background-color: #fff;
}

.imageWrapper {
  position: relative;
}

.previewButton {
  position: absolute;
  bottom: 10px;
  left: 70px;
  color: white;
  padding: 5px 10px;
  border-radius: 5px;
  font-size: 1rem;
  font-weight: 600;
  align-items: center;
}

.tab-menu {
  display: flex;
  margin-bottom: 10px;
}

.tab-menu span {
  flex: 1;
  text-align: center;
  cursor: pointer;
  padding: 10px;
  font-weight: bold;
}

.tab-menu .active {
  color: black;
  border-bottom: 2px solid #000;
}

.cardBody,
.businessCard {
  padding: 0.8rem;
}

h2 {
  font-size: 1em;
  margin-bottom: 10px;
}

p {
  margin: 0;
  padding: 5px 0;
  font-size: 0.9em;
}

.learn-more {
  color: #5624d0;
  text-decoration: underline;
  display: inline;
}

.btn-primary {
  background-color: #a435f0;
  color: #fff;
  padding: 10px;
  border: none;
  cursor: pointer;
  margin: 10px 10px;
  width: 90%;
}

.separator {
  display: flex;
  align-items: center;
  color: #aaa;
  font-size: 0.9rem;
}

.separator::before,
.separator::after {
  content: '';
  flex: 1;
  border-bottom: 1px solid #ccc;
  margin: 0 10px;
}

.price {
  font-weight: 700;
  font-size: 1.5rem;
}

.addToCartButton {
  border: 1px solid #000;
  color: #000;
  background-color: #fff;
  font-weight: bold;
  width: 100%;
  padding: 10px;
  cursor: pointer;
}

.text-center {
  text-align: center;
  font-size: 0.9em;
  color: #666;
  display: flex;
  text-align: center;
  align-items: center;
  color: #aaa;
  font-size: 0.8rem;
}

.buttonsWrapper {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}

.footerButton {
  width: fit-content;
  border: none;
  border-bottom: 2px solid #5022c3;
  background-color: transparent;
  padding: 0 auto;
  height: fit-content;
  font-size: 0.8rem;
}

.coupon-section {
  display: flex;
  align-items: center;
  color: #aaa;
  font-size: 0.7em;
  margin-top: 10px;
  border: 1px dashed #d1d7dc;
}

.coupon-section-title {
  font-size: 0.8rem;
}

.remove-coupon {
  background: none;
  border: none;
  cursor: pointer;
  color: #5624d0;
  font-size: 1.2em;
}

.coupon-input {
  display: flex;
  margin-top: 10px;
}

.coupon-input input {
  flex: 1;
  padding: 5px;
  border: 1px solid #ddd;
  border-right: none;
}

.coupon-input button {
  background-color: #000;
  color: #fff;
  padding: 5px 10px;
  border: none;
  cursor: pointer;
}

.businessCard {
  text-align: left;
}

.businessCard .udemyBusinessLogo {
  width: 100px;
  margin-bottom: 10px;
}

.benefits {
  list-style: none;
  padding: 0;
}

.benefits li {
  font-size: 0.9em;
  color: #333;
  margin-top: 10px;
}

.hide {
  display: none;
}

@media only screen and (min-width: 1080px) {
  .mainContainer {
    display: initial;
  }
}
</style>