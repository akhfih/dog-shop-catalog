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
            @clickHandler="modalHandler([breed[0], breed[1]])"
          >
            <template #text>
              {{ `${breed[1].length} sub-breed` }}
            </template>
          </base-card>
        </b-col>
      </b-row>
    </b-container>
    <b-modal v-model="modalShow" title="Sub - breeds" hide-footer>
      <div v-if="subbreed[1] == ''">
        <div class="list-item" @click="detailHandler(subbreed[0])">
          {{ subbreed[0] }}
        </div>
      </div>
      <div v-else>
        <div
          v-for="breed in subbreed[1]"
          :key="breed.key"
          class="list-item"
          @click="detailHandler(breed)"
        >
          {{ breed }}
        </div>
      </div>
    </b-modal>
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
      subbreed: ['', ''],
    })

    function modalHandler(subbreeds) {
      this.subbreed = Object.values(subbreeds)
      state.modalShow = !state.modalShow
    }

    function detailHandler(breed) {
      this.$store.dispatch('getBreedImages', breed)
    }

    return {
      ...toRefs(state),
      modalHandler,
      detailHandler,
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

<style lang="scss" scoped>
.list-item {
  width: auto;
  height: 52px;
  margin-bottom: 8px;
  padding: 8px;
  display: flex;
  align-items: center;
  background: #f5f5ff;
  border-radius: 6px;
  cursor: pointer;
  /* Drop shadow/Medium */
  &:hover {
    box-shadow: 0px 4px 6px -1px rgba(16, 24, 40, 0.1),
      0px 2px 4px -2px rgba(16, 24, 40, 0.1);
  }
}
</style>
