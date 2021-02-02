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

          <li v-for="page in pages.pages" class="nav-item dropdown">
            <a class="nav-link dropdown-toggle" href="#" :id="page.title+'Dropdown'" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              {{ page.title }}
            </a>
            <div class="dropdown-menu" :aria-labelledby="page.title+'Dropdown'">
              <nuxt-link v-for="subpage in page.subpages" class="dropdown-item" :to="'../'+page.title.toLowerCase() + '/' + subpage.title.toLowerCase()">{{ subpage.title }}</nuxt-link>
            </div>
          </li>

          <li class="nav-item">
            <nuxt-link class="nav-link" to="/contact">Contact</nuxt-link>
          </li>
        </ul>
      </div>
    </nav>

    <div style="margin-top: 5vh" v-if="content.template === 'content'" class="container" v-html="content.content"></div>

    <div v-if="content.template === 'events-overview'">
      <h1>Events!</h1>
    </div>

  </div>
</template>

<script>
export default {
  async asyncData ({ $content, route }) {
    const pages = await $content('pages').fetch()
    const page_route = route.fullPath.substr(1).split('/')
    document.title = page_route[1]
    let content = ''
    for(let i = 0; i < pages.pages.length; i++){
      if(pages.pages[i].title.toLowerCase() === page_route[0]){
        for(let j = 0; j < pages.pages[i].subpages.length; j++){
          if(pages.pages[i].subpages[j].title.toLowerCase() === page_route[1]){
            content = pages.pages[i].subpages[j]
          }
        }
      }
    }

    return {
      pages, content
    }
  },
}
</script>

<style scoped>

</style>
