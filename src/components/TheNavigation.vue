<template>
  <nav id="nav" v-show="checkRoute">
    <router-link to="/">
      <img src="@/assets/logo.png/" alt="stv logo" class="logo" />
    </router-link>
    <ul class="nav-links">
      <li v-for="portfolio in portfolios" :key="portfolio.name" class="links">
        <router-link
          :to="{
            name: `PortfolioTemplate`,
            params: { slug: portfolio.slug }
          }"
          >{{ portfolio.name }}</router-link
        >
      </li>
    </ul>
  </nav>
</template>

<script>
import store from "@/store";
export default {
  data() {
    return {
      portfolios: store.portfolios
    };
  },
  computed: {
    checkRoute() {
      if (this.$route.path == `/`) {
        return false;
      } else {
        return true;
      }
    }
  }
};
</script>

<style scope>
.logo {
  width: 175px;
  height: 175px;
}
nav {
  height: 58px;
  margin: 80px;
  margin-bottom: 120px;
  display: flex;
  justify-content: space-between;
}
ul {
  width: 500px;
  display: flex;
  justify-content: space-between;
}
li {
  font-size: 48px;
  font-weight: 300;
  color: grey;
}
</style>
