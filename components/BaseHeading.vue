<template>
  <div>
    <div class="wrapper">
      <h2 class="heading"><slot name="heading"></slot></h2>
      <p class="subheading"><slot name="subheading" /></p>
    </div>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'

export default {
  setup() {
    const state = reactive({})

    return {
      ...toRefs(state),
    }
  },
}
</script>

<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  justify-items: center;
  align-items: center;
}

span {
  color: #4b4efc;
}

.heading {
  font-style: normal;
  font-weight: 700;
  font-size: 36px;
  line-height: 44px;

  text-align: center;
  letter-spacing: -0.02em;
}

.subheading {
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  text-align: center;

  color: #6b7280;
}
</style>
