<template>
  <main class="Main">
    <div class="bg__dark"></div>

    <Suspense>
      <template #default>
        <Home />
      </template>
      <template #fallback>
        <HomeSkeleton />
      </template>
    </Suspense>
  </main>
</template>

<script>
import Home from './components/Home.vue'
import HomeSkeleton from './components/HomeSkeleton.vue'

export default {
  name: 'App',
  components: {
    Home,
    HomeSkeleton
  }
}
</script>
