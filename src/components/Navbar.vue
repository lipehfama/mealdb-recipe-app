<script setup lang="ts">
import { PhForkKnife, PhList } from "@phosphor-icons/vue";

defineEmits<{
  menuToggle: [];
}>();
</script>

<template>
  <nav class="navbar" aria-label="Primary navigation">
    <a class="navbar__brand" href="/" aria-label="FastEat home">
      <PhForkKnife class="navbar__brand-icon" :size="28" weight="fill" aria-hidden="true" />
      <span aria-hidden="true">FastEat.</span>
    </a>

    <button
      class="navbar__menu-button"
      type="button"
      aria-label="Open navigation menu"
      @click="$emit('menuToggle')"
    >
      <PhList :size="30" weight="bold" aria-hidden="true" />
    </button>
  </nav>
</template>

<style scoped>
.navbar {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: min(100% - 2.5rem, var(--container-width));
  min-height: 3.75rem;
  margin-inline: auto;
  isolation: isolate;
}

.navbar::before {
  position: absolute;
  z-index: -1;
  top: 0;
  bottom: 0;
  left: 50%;
  width: 100vw;
  content: "";
  background: var(--color-primary);
  box-shadow: 0 2px 8px rgb(0 0 0 / 16%);
  transform: translateX(-50%);
}

.navbar__brand {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--color-white);
  font-size: clamp(1.35rem, 2vw, 1.8rem);
  font-weight: 800;
  letter-spacing: -0.04em;
}

.navbar__brand-icon {
  flex: 0 0 auto;
}

.navbar__menu-button {
  display: inline-grid;
  width: 2.75rem;
  height: 2.75rem;
  padding: 0;
  place-items: center;
  border: 0;
  border-radius: var(--radius-sm);
  background: transparent;
  color: var(--color-white);
}

.navbar__menu-button:hover {
  background-color: rgb(255 255 255 / 15%);
}

@media (max-width: 480px) {
  .navbar {
    width: min(100% - 1.5rem, var(--container-width));
  }
}
</style>
