<script setup>
  import {
    RouterLink,
    RouterView
  } from 'vue-router'
  import HelloWorld from './components/HelloWorld.vue'
  import Header from './components/Header.vue';
</script>

<template>
  <Header />
  <main>
    <div class="mx-auto max-w-7xl py-6 sm:px-6 lg:px-8">
      <RouterView />
    </div>
  </main>



</template>
