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
    <div class="container" style="margin-top: 5vh">
      <h1>{{ content.title }}</h1>
      <div v-if="content.template === 'content'" v-html="content.content">

      </div>
      <div class="mt-4" v-if="content.template === 'events-overview'">

        <ul class="nav nav-tabs" id="myTab" role="tablist">
          <li v-for="(item, index) in content.content" class="nav-item" role="presentation">
            <a :class="{'active' : index === 0}" class="nav-link" :id="item.year +'-tab'" data-bs-toggle="tab" :href="'#'+item.year" role="tab" :aria-controls="item.year" aria-selected="true">{{ item.year }}</a>
          </li>
        </ul>
        <div class="tab-content" id="myTabContent">
          <div :class="{'show' : index === 0, 'active' : index === 0}" v-for="(item,index) in content.content" class="tab-pane fade" :id="item.year" role="tabpanel" :aria-labelledby="item.year+'-tab'">
            <div class="mt-4" v-html="item.events"></div>

          </div>
        </div>

      </div>

    </div>




  </div>
</template>

<script>
export default {
  async asyncData ({ $content, route }) {
    const pages = await $content('pages').fetch()
    const page_route = route.fullPath.substr(1).split('/')
    let content = ''
    for(let i = 0; i < pages.pages.length; i++){
      if(pages.pages[i].link.toLowerCase() === page_route[0]){
        for(let j = 0; j < pages.pages[i].subpages.length; j++){
          if(pages.pages[i].subpages[j].link.toLowerCase() === page_route[1]){
            content = pages.pages[i].subpages[j]
          }
        }
      }
    }

    return {
      pages, content
    }
  },
  mounted() {
    var triggerTabList = [].slice.call(document.querySelectorAll('#myTab a'))
    triggerTabList.forEach(function (triggerEl) {
      var tabTrigger = new bootstrap.Tab(triggerEl)

      triggerEl.addEventListener('click', function (event) {
        event.preventDefault()
        tabTrigger.show()
      })
    })
    document.getElementsByTagName('h1').forEach(function (el){
      el.innerHTML = el.innerHTML + '<hr>'
    })
  }
}
</script>

<style scoped>

li{
  line-height: 1;
}

li p{
  margin-bottom: 0!important;
}

</style>
