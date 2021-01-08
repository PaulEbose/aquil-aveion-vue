<template>
  <div class="Skeleton">
    <div class="Skeleton__social__icons__wrapper">
      <div
        v-for="length in 4"
        :key="length"
        class="Skeleton__social__icon"
      ></div>
    </div>

    <div class="Skeleton__Main__content">
      <div class="Skeleton__brand__name"></div>
      <div class="Skeleton__featured">
        <div class="Skeleton__featured__image"></div>
      </div>

      <div class="Skeleton__navigation__list">
        <div
          v-for="page in 2"
          :key="page"
          class="Skeleton__navigation__list__item"
        ></div>
        <div class="Skeleton__navigation__image"></div>
        <div
          v-for="page in 2"
          :key="page"
          class="Skeleton__navigation__list__item"
        ></div>
      </div>
    </div>
  </div>
</template>


<style scoped>
.Skeleton {
  --color-skeleton-text: #dc5385;
  --color-skeleton-social-icon: #ffafcb;
}

.Skeleton__brand__name {
  background: var(--color-skeleton-text);
  height: 2.5rem;
  margin: 3rem auto 0;
  width: 50%;
}

.Skeleton__featured {
  background: var(--color-box-shadow);
  box-shadow: var(--color-box-shadow) -12px 12px 20px 2px;
  height: 28rem;
  margin: auto;
  margin-top: 2rem;
  max-height: 32rem;
  max-width: 28rem;
  width: 80%;
}

.Skeleton__featured__image {
  box-shadow: var(--color-box-shadow) 0 -1px 8px;
}

.Skeleton__Main__content {
  position: relative;
}

.Skeleton__navigation__image {
  background: var(--color-box-shadow);
  border-radius: 50%;
  height: 5rem;
  justify-self: center;
  width: 5rem;
}

.Skeleton__navigation__list {
  align-items: center;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  height: 3rem;
  margin: 1.5rem 0;
  padding: 0;
}

.Skeleton__navigation__list__item {
  background: var(--color-skeleton-text);
  height: 2rem;
  justify-self: center;
  width: 6rem;
}

.Skeleton__social__icon {
  background: var(--color-skeleton-social-icon);
  height: 3rem;
  margin-top: 1rem;
  width: 3rem;
}

.Skeleton__social__icons__wrapper {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  position: absolute;
  right: 1.75rem;
  top: 38%;
}
</style>