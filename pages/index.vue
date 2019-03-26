<template>
  <section class="main-container">
    <button class="main-left navigation-btn" @click="navigateTo('about')">
      <span>A</span>
      <span>B</span>
      <span>O</span>
      <span>U</span>
      <span>T</span>
    </button>
    <div class="main-middle">
      <div class="main-middle-top">
        <span>LEARN</span>
        <span>CODE</span>
        <span>GROW</span>
      </div>
      <div class="main-middle-logo-container">
        <img class="main-logo" src="../assets/logo.svg" alt="logo">
      </div>
      <div class="main-middle-bottom">
        <p class="main__title">YUNG JU RICK KIM</p>
        <p class="main__subtitle">ANYTHING TO DO WITH PROGRAMMING</p>
        <div class="main-middle-bottom-sns-container">
          <a href="https://www.linkedin.com/in/yungjurick/">
            <img src="../assets/linkedin-logo.svg" alt="linkedIn">
          </a>
          <a href="https://www.facebook.com/yungju.r.kim">
            <img src="../assets/facebook-logo.svg" alt="facebook">
          </a>
          <a href="https://github.com/yungjurick/">
            <img src="../assets/github-logo.svg" alt="github">
          </a>
        </div>
      </div>
    </div>
    <button class="main-right navigation-btn" @click="navigateTo('projects')">
      <span>P</span>
      <span>R</span>
      <span>O</span>
      <span>J</span>
      <span>E</span>
      <span>C</span>
      <span>T</span>
      <span>S</span>
    </button>
  </section>
</template>

<script>
export default {
  layout: 'default',
  methods: {
    navigateTo(param) {
      this.$router.push({
        path: `/${param}`
      })
      this.$nuxt.$loading.start()
    }
  }
}
</script>

<style lang="scss">
@import '../assets/themes.scss';
.main-container {
  font-family: $main_font;
  font-size: 32px;
  color: white;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  .navigation-btn {
    font-family: $main_font;
    width: 32px;
    height: auto;
    color: white;
    font-size: 24px;
    background-color: transparent;
    border-color: transparent;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }
  .main-left {
    margin-right: $unit_width * 160;
    transition: 0.5s;
    &:hover {
      background-color: $main_red;
    }
  }
  .main-right {
    margin-left: $unit_width * 160;
    transition: 0.5s;
    &:hover {
      background-color: $main_blue;
    }
  }
  .main-middle {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-width: 70vw;
    height: 100vh;
    .main-middle-top {
      margin-top: $unit_height * 253;
      margin-bottom: $unit_height * 40;
      span + span {
        margin-left: 60px;
      }
    }
    .main-middle-logo-container {
      height: $unit_height * 300;
      width: $unit_height * 300;
      background-color: white;
      border-radius: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      .main-logo {
        height: 70%;
      }
    }
    .main-middle-bottom {
      margin-top: $unit_height * 40;
      margin-bottom: $unit_height * 81;
      .main__title {
        font-size: 48px;
      }
      .main__subtitle {
        font-size: 22px;
      }
      .main-middle-bottom-sns-container {
        margin-top: $unit_height * 58;
        a {
          cursor: pointer;
          img {
            height: $unit_height * 60;
          }
        }
        a + a {
          margin-left: 71px;
        }
      }
    }
  }
}
</style>
