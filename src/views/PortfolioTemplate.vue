<template>
  <div>
    <!-- Button -->
    <button @click="showModal = true">contact</button>
    <transition name="fade" appear>
      <div
        class="modal-overlay"
        v-if="showModal"
        @click="showModal = false"
      ></div>
    </transition>
    <!-- Contact -->
    <transition name="slide" appear>
      <div class="modal" v-if="showModal">
        <button @click="showModal = false">close</button>
      </div>
    </transition>
    <!-- skills -->
    <section>
      <div class="skil-container">
        <h1 class="skill-title">
          {{ portfolio.skills[0] }}
          <br />
          {{ portfolio.skills[1] }}
          <br />
          {{ portfolio.skills[2] }}
        </h1>
      </div>
    </section>
    <!-- Portfolios -->
    <section>
      <div class="portfolio">
        <div
          v-for="project in portfolio.projects"
          :key="project.slug"
          class="card-container"
        >
          <h1 class="project-title">{{ project.name }}</h1>
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
    return {
      showModal: false
    };
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

//
<style scoped>
/* Contact */
button {
  appearance: none;
  outline: none;
  border: none;
  background: none;
  cursor: pointer;
  display: inline;
  padding: 25px;
  border-radius: 50px;
  background-color: red;
  box-shadow: 3px 3px rgba(0, 0, 0, 0.4);
  transition: 0.4s ease-out;
}

button:hover {
  box-shadow: 6px 6px rgba(0, 0, 0, 0.6);
}

.modal-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 98;
  background-color: rgba(0, 0, 0, 0.3);
}

.modal {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 99;
  width: 700px;
  height: 300px;
  background-color: white;
  overflow: hidden;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 0.5s;
}

.slide-enter,
.slide-leave-to {
  transform: translateY(-50%) translateX(100vw);
}

/*  Skill box */
.skil-container {
  width: 675px;
  margin: 200px 80px 80px 80px;
}
.skill-title {
  font-family: "Playfair Display", serif;
  font-size: 75px;
  text-transform: uppercase;
  line-height: 0.7;
  padding-left: 20px;
  padding-bottom: 10px;
  border-left: 5px solid black;
}

/* Project  */
.portfolio {
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
