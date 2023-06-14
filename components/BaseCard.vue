<template>
  <div>
    <b-card
      :title="title"
      :img-src="image"
      img-alt="Image"
      img-top
      tag="div"
      @click="clickHandler"
    >
      <b-card-text> <slot name="text"></slot> </b-card-text>
    </b-card>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'

export default {
  name: 'BaseCard',
  props: {
    image: { type: String, default: '' },
    title: { type: String, default: '' },
    text: { type: String, default: '' },
  },
  emits: ['clickHandler'],
  setup(props, { emit }) {
    const state = reactive({})

    const clickHandler = () => {
      emit('clickHandler')
    }

    return {
      ...toRefs(state),
      clickHandler,
    }
  },
}
</script>

<style lang="scss" scoped>
.card {
  border-radius: 12px;
  padding: 0.5rem !important;
  max-width: 176px;
  max-height: 223px;
  box-shadow: 0px 1px 2px rgba(16, 24, 40, 0.05);
  border: 1px solid #f9fafb;
  margin: auto;

  cursor: pointer;

  &:hover {
    border: 1px solid #f9fafb;
    box-shadow: 0px 25px 50px -12px rgba(1, 72, 215, 0.25);
  }
  img {
    border-radius: 6px;
    max-width: 160px;
    max-height: 153px;
    min-height: 153px;
    object-fit: contain;
    object-fit: cover;
    border: 1px solid #f9fafb;
  }

  &-body {
    padding: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  &-title {
    font-style: normal;
    font-weight: 500;
    font-size: 16px;
    line-height: 24px;

    display: flex;
    align-items: center;
    text-align: center;
    font-feature-settings: 'salt' on;

    color: #111827;
    margin-bottom: 0;
  }
  &-text {
    font-weight: 500;
    font-size: 12px;
    line-height: 20px;
    color: #6b7280;
  }
}
</style>
