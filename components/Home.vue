<!-- Please remove this file from your project -->
<template>
  <div>
    <TheHero></TheHero>
    <BaseHeading>
      <template #heading>The <span>Dog</span> breed</template>
      <template #subheading
        >Siapa yang mencintaiku akan mencintai anjingku juga.</template
      >
    </BaseHeading>
    <base-card
      image="https://images.dog.ceo/breeds/hound-afghan/n02088094_3937.jpg"
      title="Terries"
      text="123 sub-breeds"
      @clickHandler="tes"
    ></base-card>

    <b-modal v-model="modalShow">Hello From Modal!</b-modal>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'
export default {
  name: 'NuxtHome',
  setup() {
    const state = reactive({
      modalShow: false,
    })
    function tes() {
      state.modalShow = !state.modalShow
    }

    return {
      ...toRefs(state),
      tes,
    }
  },
}
</script>
