<template>
  <Suspense>
    <template #default>
      <Home />
    </template>
    <template #fallback>
      <div class="Loading">
        <span>Loading...</span>
      </div>
    </template>
  </Suspense>
</template>

<script>
import Home from './components/Home.vue'

export default {
  name: 'App',
  components: {
    Home
  }
}
</script>
