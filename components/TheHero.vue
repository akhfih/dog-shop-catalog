<template>
  <div>
    <div class="hero d-flex flex-column align-content-center">
      <div class="hero__text">
        <h1>
          {{ content.headerBefore
          }}<span class="">{{ content.headerMiddle }}</span
          >{{ content.headerAfter }}
        </h1>
        <p>{{ content.text }}</p>
      </div>
      <div hero__image>
        <img :src="image" alt="hero_image" />
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'
import image from '@/assets/images/hero_image.svg'
export default {
  setup() {
    const state = reactive({
      content: {
        headerBefore: 'A simple ',
        headerMiddle: 'Dog',
        headerAfter: ' Shop Catalog',
        text: 'Anjing itu seorang pria sejati; Saya berharap untuk pergi ke surganya, bukan surga manusia.',
      },
    })

    return {
      ...toRefs(state),
      image,
    }
  },
}
</script>

<style lang="scss" scoped>
.hero {
  max-width: 1216px;
  margin: 64px auto;
  align-items: center;

  &__text {
    max-width: 586px;
    color: #111827;
    text-align: center;
    h1 {
      font-style: italic;
      font-weight: 700;
      font-size: 52px;
      line-height: 56px;

      letter-spacing: -0.02em;
      span {
        color: #4b4efc;
      }
    }
    p {
      font-style: italic;
      font-weight: 400;
      font-size: 18px;
      line-height: 28px;
      color: #374151;
    }
  }
}
</style>
