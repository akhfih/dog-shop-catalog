<!-- Please remove this file from your project -->
<template>
  <div>
    <TheHero></TheHero>
    <TheBreedList></TheBreedList>
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
