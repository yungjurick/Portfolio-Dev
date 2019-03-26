<template>
  <section class="projects-container">
    <h1 class="projects-title">
      PROJECTS
      <span class="projects-underline">_</span>
    </h1>
    <hr class="projects--hr">
    <div class="projects-inner-container">
      <div v-for="data in projectsData" :key="data.id" class="project-container">
        <img :src="data.projectImages[0].url" alt="image" class="project-image">
        <h1>{{ data.projectTitle }}</h1>
        <p>{{ data.projectDescription }}</p>
      </div>
    </div>
  </section>
</template>

<script>
import Strapi from 'strapi-sdk-javascript/build/main'
const apiUrl = process.env.API_URL || 'http://localhost:1337'
const strapi = new Strapi(apiUrl)
export default {
  layout: 'information',
  data() {
    return {
      query: ''
    }
  },
  computed: {
    projectsData() {
      return this.$store.getters.list
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.finish()
    })
  },
  async fetch({ store }) {
    store.commit('emptyList')
    const response = await strapi.request('post', '/graphql', {
      data: {
        query: `query {
          projects(sort: "projectStartDate:DESC") {
            id
            projectTitle
            projectDescription
            projectImages {
              url
            }
          }
        }
        `
      }
    })
    response.data.projects.forEach(project => {
      project.projectImages.forEach(image => {
        image.url = `${apiUrl}${image.url}`
      })
      store.commit('add', {
        id: project.id,
        ...project
      })
    })
  }
}
</script>

<style lang="scss">
@import '../assets/themes.scss';
.projects-container {
  margin: ($unit_height * 71) ($unit_width * 60);
  font-family: $main_font;
  .projects-title {
    font-size: 72px;
    .projects-underline {
      margin-left: -24px;
      color: $main_red;
    }
  }
  .projects--hr {
    width: $unit_width * 104;
    height: 10px;
    background-color: black;
    border: none;
    margin: 50px 0 70px 0;
  }
  .projects-inner-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(640px, 1fr));
    width: 100%;
    .project-container {
      position: relative;
      padding: 32px;
      text-align: center;
      min-width: 640px;
      background-repeat: no-repeat;
      background-size: cover;
      background-position: center;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 355px;
      transition: all 2s;
      cursor: pointer;
      h1 {
        margin-bottom: 10px;
        font-size: 32px;
      }
      p {
        font-size: 16px;
      }
      h1,
      p {
        z-index: 10;
        opacity: 0;
        transition: all 1s;
      }
      &:hover {
        .project-image {
          opacity: 0.1;
        }
        h1,
        p {
          opacity: 1;
        }
      }
      .project-image {
        transition: all 0.5s;
        position: absolute;
        height: 100%;
        width: 100%;
      }
    }
  }
}
</style>
