<template>
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

  <div class="Main__content">
    <h1 class="brand__name">{{ brandName }}</h1>

    <figure class="featured">
      <img
        src="../assets/model.png"
        :alt="`${brandName}: Freshly Squeezed`"
        class="featured__image"
      />
    </figure>

    <nav>
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

        <div class="navigation__list__image__wrapper" aria-hidden="true">
          <!-- decorative image -->
          <img
            src="../assets/nav-img.jpg"
            alt=""
            class="navigation__list__image"
          />
        </div>

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
  </div>
</template>

<script>
import EmailIcon from "../assets/email.svg";
import InstagramIcon from "../assets/instagram.svg";
import SnapchatIcon from "../assets/snapchat.svg";
import TwitterIcon from "../assets/twitter.svg";

export default {
  name: "Home",
  async setup() {
    // async setup(ctx, props) {
    const navigationPagesLeft = ["home", "about"];
    const navigationPagesRight = ["gallery", "contact"];
    let data;

    const fetchData = async () => {
      const res = await fetch("https://hirng-x2021.glitch.me/api");
      if (res.ok) {
        return await res.json();
      } else {
        console.error("Incompatiable data.");
      }
    };

    try {
      data = await fetchData();
    } catch {
      console.error("Error fetching data.");
    }

    let socialMedia = [];
    for (const platform in data.social_media) {
      let href = `https://${platform}.com/${data.social_media[platform]}`;
      let icon = "";

      switch (platform) {
        case "email":
          href = `mailto://${data.social_media[platform]}`;
          icon = EmailIcon;
          break;
        case "instagram":
          icon = InstagramIcon;
          break;
        case "snapchat":
          icon = SnapchatIcon;
          break;
        case "twitter":
          icon = TwitterIcon;
          break;
        default:
          break;
      }

      socialMedia.push({ href, icon, platform });
    }

    return {
      brandName: data.name,
      navigationPagesLeft,
      navigationPagesRight,
      socialMedia,
    };
  },
};
</script>
