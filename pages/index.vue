<template>
  <div class="container">
    <nuxt-content :document="homepage" />
  </div>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const homepage = await $content('home').fetch()

    return {
      homepage
    }
  }
}
</script>

<style>


</style>
