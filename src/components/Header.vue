<script setup lang="ts">
import Navbar from "./Navbar.vue";
import SearchForm from "./SearchForm.vue";

const emit = defineEmits<{
  menuToggle: [];
  search: [query: string];
}>();
</script>

<template>
  <header class="site-header">
    <Navbar @menu-toggle="emit('menuToggle')" />

    <section id="main-content" class="site-header__hero" aria-labelledby="hero-title">
      <div class="site-header__content">
        <h1 id="hero-title">What are your favorite cuisines?</h1>
        <p>Discover amazing recipes from around the world</p>
        <SearchForm @search="emit('search', $event)" />
      </div>
    </section>
  </header>
</template>

<style scoped>
.site-header {
  min-height: 24rem;
  color: var(--color-white);
  background:
    linear-gradient(rgb(0 0 0 / 48%), rgb(0 0 0 / 58%)),
    url("../assets/images/header_image.jpg") center / cover;
}

.site-header__hero {
  display: grid;
  min-height: 20.25rem;
  padding: 2.5rem 1.25rem 4rem;
  place-items: center;
}

.site-header__content {
  display: grid;
  justify-items: center;
  width: min(100%, 50rem);
  text-align: center;
}

.site-header h1 {
  max-width: 46rem;
  font-size: clamp(2rem, 4vw, 3.25rem);
  font-weight: 800;
  letter-spacing: -0.03em;
}

.site-header p {
  margin-top: 0.5rem;
  font-size: clamp(1rem, 1.6vw, 1.2rem);
}

.site-header :deep(.recipe-search) {
  margin-top: 1.5rem;
}

@media (max-width: 480px) {
  .site-header {
    min-height: 22rem;
  }

  .site-header__hero {
    min-height: 18.25rem;
    padding-inline: 0.75rem;
  }
}
</style>
