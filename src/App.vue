<template>
  <div id="app">
    <div id="nav">
      <TheNavigation />
    </div>
    <router-view :key="$route.path" />
  </div>
</template>

<script>
import TheNavigation from "@/components/TheNavigation";
export default {
  components: {
    TheNavigation
  }
};
</script>
>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: "Open Sans", sans-serif;
}
body {
  overflow-x: hidden;
}
a {
  text-decoration: none;
}
a:active {
  color: none;
}
a:visited {
  text-decoration: none;
}

li {
  list-style-type: none;
}
</style>
