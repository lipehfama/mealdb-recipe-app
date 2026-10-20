<script setup lang="ts">
import { ref } from "vue";
import { PhMagnifyingGlass } from "@phosphor-icons/vue";

const query = ref("");

const emit = defineEmits<{
  search: [query: string];
}>();

function submitSearch() {
  const searchTerm = query.value.trim();

  if (searchTerm) {
    emit("search", searchTerm);
  }
}
</script>

<template>
  <form class="recipe-search" role="search" @submit.prevent="submitSearch">
    <label class="sr-only" for="recipe-search">Search recipes</label>
    <input
      id="recipe-search"
      v-model="query"
      class="recipe-search__input"
      type="search"
      name="recipe"
      placeholder="Search recipes here ..."
      autocomplete="off"
      required
    />
    <button class="recipe-search__button" type="submit" aria-label="Search recipes">
      <PhMagnifyingGlass :size="24" weight="bold" aria-hidden="true" />
    </button>
  </form>
</template>

<style scoped>
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

.recipe-search {
  display: flex;
  align-items: center;
  width: min(100%, 37.5rem);
  min-height: 3.75rem;
  padding: 0.25rem;
  border: 1px solid rgb(255 255 255 / 65%);
  border-radius: var(--radius-full);
  background: var(--color-white);
  box-shadow: 0 8px 24px rgb(0 0 0 / 18%);
}

.recipe-search__input {
  flex: 1;
  width: 100%;
  min-width: 0;
  padding: 0.75rem 1.25rem;
  border: 0;
  outline: 0;
  background: transparent;
  color: var(--color-dark);
}

.recipe-search__input::placeholder {
  color: var(--color-gray);
}

.recipe-search__button {
  display: inline-grid;
  flex: 0 0 auto;
  width: 3.1rem;
  height: 3.1rem;
  padding: 0;
  place-items: center;
  border: 0;
  border-radius: 50%;
  background: var(--color-primary);
  color: var(--color-white);
  transition: background-color var(--transition-base), transform var(--transition-base);
}

.recipe-search__button:hover {
  background: var(--color-primary-hover);
  transform: scale(1.04);
}

@media (max-width: 480px) {
  .recipe-search {
    min-height: 3.5rem;
  }

  .recipe-search__input {
    padding-inline: 0.85rem;
  }

  .recipe-search__button {
    width: 2.75rem;
    height: 2.75rem;
  }
}
</style>
