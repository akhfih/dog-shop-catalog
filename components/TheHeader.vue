<template>
  <div>
    <div class="wrapper">
      <b-navbar toggleable="lg" type="light">
        <b-navbar-brand href="#"><AsudogLogo></AsudogLogo></b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto">
            <b-nav-item
              ><nuxt-link class="nuxt-link" exact to="/"
                >Home</nuxt-link
              ></b-nav-item
            >

            <b-nav-item
              ><nuxt-link class="nuxt-link" exact to="/About"
                >About</nuxt-link
              ></b-nav-item
            >
          </b-navbar-nav>

          <!-- Right aligned nav items -->
        </b-collapse>
      </b-navbar>
    </div>
  </div>
</template>

<script>
import { reactive, toRefs } from 'vue'

export default {
  setup() {
    const state = reactive({
      count: 0,
    })

    return {
      ...toRefs(state),
    }
  },
}
</script>

<style lang="scss" scoped>
:deep(nav) {
  max-width: 1216px;
  margin: auto;
}

:deep(.nav-link) {
  font-style: normal;
  font-weight: 600;
  font-size: 1rem;
  line-height: 24px;
}

.wrapper {
  box-shadow: 0px 1px 3px rgba(16, 24, 40, 0.1),
    0px 1px 2px -1px rgba(16, 24, 40, 0.1);
}

.nuxt-link {
  color: #111827;
  &:hover {
    text-decoration: none;
    color: #4b4efc;
  }
}
</style>
