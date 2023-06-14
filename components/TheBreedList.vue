<template>
  <div>
    <BaseHeading class="mb-4">
      <template #heading>The <span>Dog</span> breed</template>
      <template #subheading
        >Siapa yang mencintaiku akan mencintai anjingku juga.</template
      >
    </BaseHeading>
    <b-container class="bv-example-row">
      <b-row cols="2" cols-sm="3" cols-md="4" cols-lg="6">
        <b-col v-for="breed in list" :key="breed.key" class="pb-4">
          <base-card
            image="https://images.dog.ceo/breeds/hound-afghan/n02088094_1003.jpg"
            :title="breed[0]"
            @clickHandler="modalHandler"
          >
            <template #text>
              {{ `${breed[1].length} sub-breed` }}
            </template>
          </base-card>
        </b-col>
      </b-row>
    </b-container>
    <b-modal v-model="modalShow">Hello From Modal!</b-modal>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'
import { mapState, mapActions } from 'vuex'

export default {
  setup() {
    const state = reactive({
      modalShow: false,
      breedList: [],
    })

    function modalHandler() {
      state.modalShow = !state.modalShow
    }

    return {
      ...toRefs(state),
      modalHandler,
    }
  },
  computed: {
    ...mapState(['breedsdatafetch']),
    list: function () {
      return this.$store.getters.getterBreeds
    },
  },
  beforeCreate() {
    this.$store.dispatch('getBreedsData')
  },
  mounted() {
    this.getImage()
  },
  methods: {
    ...mapActions(['getBreedsData']),
    getImage: async function () {
      const data = await fetch('https://dog.ceo/api/breed/hound/images/random')
        .then((response) => response.json())
        .then((data) => {
          return data
        })

      return data
    },
  },
}
</script>

<style lang="scss" scoped></style>
