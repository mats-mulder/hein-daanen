<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a class="navbar-brand" href="/">Hein Daanen</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <nuxt-link class="nav-link" to="/">Home</nuxt-link>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="academicDropdown" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              Academic
            </a>
            <div class="dropdown-menu" aria-labelledby="academicDropdown">
              <nuxt-link v-for="item in academic" class="dropdown-item" :to="'/academic/'+item.title">{{ item.title }}</nuxt-link>
            </div>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="mediaDropdown" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              Media
            </a>
            <div class="dropdown-menu" aria-labelledby="mediaDropdown">
              <nuxt-link v-for="item in media" class="dropdown-item" :to="'/media/'+item.title">{{ item.title }}</nuxt-link>
            </div>
          </li>
          <li class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" id="personalDropdown" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              Personal
            </a>
            <div class="dropdown-menu" aria-labelledby="personalDropdown">
              <nuxt-link v-for="item in personal" class="dropdown-item" :to="'/personal/'+item.title">{{ item.title }}</nuxt-link>
            </div>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link" to="/contact">Contact</nuxt-link>
          </li>
        </ul>
      </div>
    </nav>

    <div class="container mt-5 mb-5">
      <nuxt-content :document="homepage" />
    </div>
  </div>

</template>

<script>
export default {
  async asyncData ({ $content }) {
    const homepage = await $content('home').fetch()
    const academic =  await $content('academic').only(['title']).fetch()
    const media =  await $content('media').only(['title']).fetch()
    const personal =  await $content('personal').only(['title']).fetch()
    return {
      homepage, academic, media, personal
    }
  }
}
</script>

<style>


</style>
