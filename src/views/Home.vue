<template>
  <div class="home">
    <div class="linkContainer">
      <div
        v-for="portfolio in portfolios"
        :key="portfolio.name"
        class="nameBox"
      >
        <router-link
          :to="{
            name: `PortfolioTemplate`,
            params: { slug: portfolio.slug }
          }"
        >
          <h1 class="nameBox__name">{{ portfolio.name }}</h1>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import store from "@/store";

export default {
  data() {
    return {
      portfolios: store.portfolios
    };
  },
  name: "Home",
  components: {}
};
</script>

<style scoped>
.linkContainer {
  width: 100%;
  height: 100vh;
  display: flex;
}

.nameBox {
  width: 100%;
  height: 100%;
  border: 1px solid black;
  cursor: pointer;

  /* Flexing */
  display: flex;
  justify-content: center;

  /* Animation */
  transition-duration: 500ms;
}
.nameBox:hover {
  width: 120%;
}

.nameBox__name {
  font-size: 144px;
  font-weight: 100;
  text-transform: uppercase;
  letter-spacing: -95px;

  color: black;
  writing-mode: vertical-rl;
  text-orientation: upright;
  margin-top: 30%;
}
</style>
