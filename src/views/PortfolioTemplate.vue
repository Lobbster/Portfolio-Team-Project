<template>
  <div>
    <section>
      <div class="skil-container">
        <h1 class="skill-title">{{portfolio.skills[0]}}</h1>
        <h1 class="skill-title">{{portfolio.skills[1]}}</h1>
        <h1 class="skill-title">{{portfolio.skills[2]}}</h1>
      </div>
    </section>
    <section>
      <div class="portfolio">
        <div v-for="project in portfolio.projects" :key="project.slug" class="card-container">
          <h1 class="project-title">{{project.name}}</h1>
          <router-link
            :to="{
              name: `ProjectTemplate`,
              params: { projectSlug: project.slug }
            }"
          ></router-link>
          <div class="cards">
            <router-link
              :to="{
              name: `ProjectTemplate`,
              params: { projectSlug: project.slug }
            }"
            >
              <div class="image-card"></div>
            </router-link>

            <router-link
              :to="{
              name: `ProjectTemplate`,
              params: { projectSlug: project.slug }
            }"
            >
              <div class="image-card"></div>
            </router-link>
            <router-link
              :to="{
              name: `ProjectTemplate`,
              params: { projectSlug: project.slug }
            }"
            >
              <div class="image-card"></div>
            </router-link>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import store from "@/store.js";
export default {
  data() {
    return {};
  },
  props: {
    slug: {
      type: String,
      required: true
    }
  },
  computed: {
    portfolio() {
      return store.portfolios.find(portfolio => portfolio.slug === this.slug);
    }
  }
};
</script>

<style scoped>
.skil-container {
  width: 675px;
  height: 275px;
  margin: 200px 80px;
  background-color: grey;
}

.portfolio {
  margin-top: 200px;
  width: 100%;
}
.card-container {
  margin-bottom: 100px;
  position: relative;
}
.cards {
  display: flex;
  overflow: hidden;
}
.image-card {
  width: 600px;
  height: 400px;
  margin: 5px;
  background-color: teal;
}
.project-title {
  font-size: 150px;
  color: white;
  font-family: "Sail", cursive;
  text-transform: lowercase;
  z-index: 1;
  position: absolute;

  bottom: -40px;
  right: 0px;
}
</style>
