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
            <a class="nav-link dropdown-toggle" href="#" id="publicationsDropdown" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
              Academic
            </a>
            <div class="dropdown-menu" aria-labelledby="publicationsDropdown">
              <nuxt-link class="dropdown-item" to="/cv">Curriculum Vitae</nuxt-link>
              <nuxt-link class="dropdown-item" to="/publications">Publications</nuxt-link>
              <nuxt-link class="dropdown-item" to="/thesis">Thesis</nuxt-link>
              <nuxt-link class="dropdown-item" to="/inauguration-thermal">Inauguration Prof. Thermal Physiology</nuxt-link>
              <nuxt-link class="dropdown-item" to="/inauguration-fashion">Inauguration Prof. Fashion Research & Technology</nuxt-link>
              <nuxt-link class="dropdown-item" to="/lectures">Lezingen/Lectures</nuxt-link>
            </div>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link" to="/media">Media</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link" to="/family">Family</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link class="nav-link" to="/contact">Contact</nuxt-link>
          </li>
        </ul>
      </div>

    </nav>
    <Nuxt style="margin-top: 5vh"></Nuxt>
  </div>
</template>

<style>


</style>
