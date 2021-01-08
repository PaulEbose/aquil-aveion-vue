<template>
  <div class="Skeleton">
    <div class="Skeleton__social__icons__wrapper">
      <div v-for="length in 4" :key="length" class="Skeleton__social__icon"></div>
    </div>

    <div class="Skeleton__Main__content">
      <div class="Skeleton__brand__name"></div>
      <div class="Skeleton__featured">
        <div class="Skeleton__featured__image"></div>
      </div>

      <div class="Skeleton__navigation__list">
        <div v-for="page in 2" :key="page" class="Skeleton__navigation__list__item"></div>
        <div class="Skeleton__navigation__image"></div>
        <div v-for="page in 2" :key="page" class="Skeleton__navigation__list__item"></div>
      </div>
    </div>
  </div>
</template>
