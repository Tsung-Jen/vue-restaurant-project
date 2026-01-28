<!-- <template>
  <div class="min-h-screen bg-red-500 text-3xl text-white p-10">
    Tailwind Absolute Test
  </div>
</template>

<script setup lang="ts"></script> -->

<!-- src/App.vue -->
<template>
  <AppHeader />
  <router-view />
  <AppFooter />
</template>

<script setup lang="ts">
  import AppHeader from './components/AppHeader.vue';
  import AppFooter from './components/AppFooter.vue';
</script>
