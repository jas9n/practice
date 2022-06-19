<template>
  <div id="app" class="h-screen flex flex-col justify-center items-center">
    <div id="title" class="p-6 flex flex-col justify-center items-center">
      <h1 class="text-5xl pb-1">Home</h1>
      <p class="text-xl">Small JS Projects using Nuxt</p>
    </div>
    <div id="links" class="grid grid-cols-2 grid-rows-auto gap-4 md:grid-cols-3">
      <NuxtLink to="/calculator"><page-link class="hover:bg-purple-300">Calculator</page-link></NuxtLink>
      <NuxtLink to="/stopwatch"><page-link class="hover:bg-red-300">Stopwatch</page-link></NuxtLink>
      <NuxtLink to="/randomizer"><page-link class="hover:bg-indigo-300">Random Color</page-link></NuxtLink>
    </div>
  </div>
</template>

<script>
import RouterLink from '../components/PageLink.vue'
export default {
  components: { RouterLink },
  name: 'Home',
}
</script>
