<template>
  <div class="home">
    <div class="linkContainer">
      <div v-for="portfolio in portfolios" :key="portfolio.name">
        <router-link
          :to="{
            name: `PortfolioTemplate`,
            params: { slug: portfolio.slug }
          }"
        >
          <div class="nameBox">
            <h1 class="nameBox__name">{{ portfolio.name }}</h1>
          </div>
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

  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

.nameBox {
  height: 100%;
  border: 1px solid black;
  cursor: pointer;

  display: flex;
  justify-content: center;
}

.nameBox__name {
  font-size: 144px;
  font-weight: 100;
  text-transform: uppercase;
  letter-spacing: -95px;

  color: black;
  writing-mode: vertical-rl;
  text-orientation: upright;
  margin-top: 25%;
}
</style>
