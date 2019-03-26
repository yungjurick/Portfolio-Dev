<template>
  <section>
    <transition name="layout" mode="out-in">
      <nuxt/>
    </transition>
  </section>
</template>

<style lang="scss">
@import '../assets/themes.scss';
*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}
</style>
