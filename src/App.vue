<template>
  <main class="Main">
    <h1>{{ brandName }}</h1>

    <figure class="featured">
      <img
        src="./assets/model.png"
        :alt="`${brandName}: Freshly Squeezed`"
        class="featured__image"
      />
    </figure>

    <ul class="social__icons">
      <li v-for="{ href, icon, platform } in socialMedia" :key="platform">
        <a :href="href" class="social__icons__link">
          <img
            :src="icon"
            :alt="`Reach us on ${platform}`"
            class="social__icons__image"
          />
        </a>
      </li>
    </ul>

    <nav class="navigation">
      <ul class="navigation__list">
        <li
          v-for="page in navigationPagesLeft"
          :key="page"
          class="navigation__list__item"
        >
          <a :href="`/${page}`" class="navigation__list__link">
            {{ page }}
          </a>
        </li>

        <li class="navigation__list__item" aria-hidden="true">
          <!-- decorative image -->
          <img src="./assets/navImg.png" alt="" class="navigation__list__image" />
        </li>

        <li
          v-for="page in navigationPagesRight"
          :key="page"
          class="navigation__list__item"
        >
          <a :href="`/${page}`" class="navigation__list__link">
            {{ page }}
          </a>
        </li>
      </ul>
    </nav>
  </main>
</template>

<script>
const sampleData = {
  name: 'AQUILA AVEION',
  social_media: {
    twitter: 'aquilaveion',
    instagram: 'aquilaveionofficial',
    snapchat: 'aquilaveionsnaps',
    email: 'aquilaveion@aquil.com'
  }
}

export default {
  name: 'App',
  components: {
    Image
  },
  setup() {
    const navigationPagesLeft = ['home', 'about']
    const navigationPagesRight = ['gallery', 'contact']
    // @todo: fetch from api
    const { name, social_media } = { ...sampleData }
    let socialMedia = []

    for (const platform in social_media) {
      let href = `https://${platform}.com/${social_media[platform]}`

      if (platform === 'email') {
        href = `mailto://${social_media[platform]}`
      }

      socialMedia.push({ href, icon: `/src/assets/${platform}.svg`, platform })
    }

    return {
      brandName: name,
      navigationPagesLeft,
      navigationPagesRight,
      socialMedia
    }
  }
}
</script>
