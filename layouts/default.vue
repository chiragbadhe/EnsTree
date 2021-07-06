<template>
  <div>
      <AppHeader />
      <Nuxt />
      <AppFooter />
  </div>
</template>

<script>
import AppFooter from '~/components/global/AppFooter.vue'
import AppHeader from '~/components/global/AppHeader.vue'
export default {
  components: { AppHeader, AppFooter },

}
</script>

<style>

</style>