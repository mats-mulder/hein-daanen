<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <a  style="font-weight: 500" class="navbar-brand" href="/">Hein Daanen</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <nuxt-link class="nav-link" to="/">Home</nuxt-link>
          </li>

          <li v-for="page in pages.pages" class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" :id="page.link+'Dropdown'" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              {{ page.title }}
            </a>
            <div class="dropdown-menu" :aria-labelledby="page.link+'Dropdown'">
              <nuxt-link v-for="subpage in page.subpages" class="dropdown-item" :to="'../'+page.link.toLowerCase() + '/' + subpage.link.toLowerCase()">{{ subpage.title }}</nuxt-link>
            </div>
          </li>

          <li class="nav-item">
            <nuxt-link class="nav-link" to="/contact">Contact</nuxt-link>
          </li>
        </ul>
      </div>
    </nav>

    <div class="container mt-4 mb-5" v-html="homepage.content">

    </div>
  </div>

</template>

<script>
export default {
  head: {
    title: 'Home',
  },
  async asyncData ({ $content }) {
    const homepage = await $content('home').fetch()
    const pages = await $content('pages').fetch()
    return {
      homepage, pages
    }
  },
  mounted() {
    document.getElementsByTagName('h1').forEach(function (el){
      el.innerHTML = el.innerHTML + '<hr>'
    })
  }
}
</script>

<style>


</style>
