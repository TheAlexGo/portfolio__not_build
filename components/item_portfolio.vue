<template>
  <div class="card-portfolio d-flex mt-2 mb-2">
    <transition name="fade">
      <Modal v-if="isPopShow"
             @closePopup="closePopup"
             :portfolio_data="productData" />
    </transition>
    <div class="d-flex flex-column card-portfolio__body">
      <a @click="showPopup" style="
        display: block;
        overflow: hidden;
        cursor: pointer;"

      >
        <img
          class="image_img"
          :key="productData.id"
          :src="productData.photo"
          :alt="productData.name">
      </a>
      <span class="item_text">{{ productData.name }}</span>
      <p class="text-secondary">{{ productData.time }}</p>
    </div>
  </div>
</template>

<script>
import Modal from "../components/popup";
export default {
  name: "item_portfolio",
  props: {
    productData: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  components: {
    Modal
  },
  data () {
    return {
      isActive: true,
      isPopShow: false,
      width_img: 270,
      height_img: 270
    }
  },
  methods: {
    showPopup () {
      this.isPopShow = true;
      document.body.style.overflow = 'hidden';
    },
    closePopup () {
      this.isPopShow = false;
      document.body.style.overflow = '';
    }
  }
}
</script>

<style scoped lang="scss">
body {
  padding: 0;
}

.image {
  padding: 0 15px;
}

@media screen and (max-width: 576px) {
  .image {
    margin: 0 auto;
    transition: 1s;
  }
}

.image_img {
  @media screen and (max-width: 767px) and (min-width: 540px) {
    max-width: 200px;
    max-height: 200px;
  }

  @media screen and (max-width: 540px) {
    max-width: 300px;
    max-height: 300px;
  }

  @media screen and (min-width: 767px) {
    max-width: 255px;
    max-height: 255px;
  }

  width: 100%;
  object-fit: cover;
  object-position: top;
  -moz-transition: all 0.3s ease-out;
  -o-transition: all 0.3s ease-out;
  -webkit-transition: all 0.3s ease-out;
}

.image_img:hover {
  -webkit-transform: scale(1.2);
  -moz-transform: scale(1.2);
  -o-transform: scale(1.2);
}

.fade-enter-active,
.fade-leave-active {
  top: 0;
  opacity: 1;
  transition: 0.4s;
}

.fade-enter,
.fade-leave-to {
  position: fixed;
  top: -300px;
  opacity: 0;
}

.card-portfolio {
  &__body {
    padding: 0 15px;
  }
}
</style>
