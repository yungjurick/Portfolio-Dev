<template>
  <transition name="layout" mode="out-in">
    <div class="main-layout">
      <div class="main-bg"/>
      <nuxt class="main-view"/>
    </div>
  </transition>
</template>

<style lang="scss">
@import '../assets/themes.scss';

.main-layout {
  .main-view {
    z-index: 1;
  }
  .main-bg {
    position: fixed;
    z-index: -1;
    background-color: $main_blue;
    top: 0;
    border-bottom: solid 50vh $main_red;
    border-right: solid 50vw $main_red;
    border-left: solid 50vw transparent;
    border-top: solid 50vh transparent;
  }
}

html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}
</style>
