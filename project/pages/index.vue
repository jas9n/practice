<template>
  <div id="app" class="h-screen flex flex-col justify-center items-center">
    <div id="title" class="p-6 flex flex-col justify-center items-center">
      <h1 class="text-5xl">Home</h1>
      <p class="text-xl">Small JS Projects using Nuxt</p>
    </div>
    <div id="links" class="grid grid-cols-3 grid-rows-auto gap-4">
      <NuxtLink to="/calculator"><page-link>Calculator</page-link></NuxtLink>
      <NuxtLink to="/stopwatch"><page-link>Stopwatch</page-link></NuxtLink>
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
