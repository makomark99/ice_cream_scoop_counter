<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
      <nav>
       <RouterLink to="/">Főoldal</RouterLink>
       <RouterLink to="/icecream_counter">Gombócok</RouterLink>
      </nav>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}


nav {
  width: 70%;
  
  text-align: center;
  margin-top: 2rem;
}

nav a {
  color: var(--color-text);
  font-size: 36px;
}

nav a:hover {
  color: yellowgreen;
  background-color: transparent;
  text-shadow: 8px 8px 8px yellowgreen;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a {
  border: 0;
}

@media (min-width: 1024px) {

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
