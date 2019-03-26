<template>
  <section class="about-container">
    <h1 class="about-title">
      ABOUT
      <span class="about-underline">_</span>
    </h1>
    <hr class="about--hr">
    <div class="about-inner-container">
      <div class="about-description">
        <p>
          Hi, I am Yung Ju Rick Kim, a full-time student from South Korea majoring in Computer Science at New York University Abu Dhabi.
        </p>
        <p>
          My interest lies in creating new things using the current web technologies or anything that relates to programming. Until now, I have been exploring in the fields of web programming, primarily in the area of front-end.
        </p>
        <p>
          I am a triple smiley-person with high level of optimism at heart. And, I love to spend time listening to jazz and new age.
        </p>
      </div>
      <div class="about-image">
        <img src="@/assets/self-image.jpg" alt="image">
      </div>
    </div>
  </section>
</template>

<script>
export default {
  layout: 'information'
}
</script>

<style lang="scss">
@import '../assets/themes.scss';
.about-container {
  margin: ($unit_height * 71) ($unit_width * 60);
  font-family: $main_font;
  .about-title {
    font-size: 72px;
    .about-underline {
      margin-left: -24px;
      color: $main_blue;
    }
  }
  .about--hr {
    width: $unit_width * 104;
    height: 10px;
    background-color: black;
    border: none;
    margin: 50px 0 70px 0;
  }
  .about-inner-container {
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    .about-description {
      flex: 1 1 $unit_width * 638;
      margin-right: 99px;
      font-size: 20px;
      line-height: 1.8;
      text-align: justify;
      p + p {
        margin-top: 16px;
      }
    }
    .about-image {
      flex: 1 1 40%;
      display: flex;
      justify-content: center;
      align-items: center;
      img {
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
        height: 318px;
        width: 318px;
      }
    }
  }
}
</style>
