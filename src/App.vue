<template>
  <div id="app">
    <img src="./assets/logo.svg" class="logo">
    <search/>
  </div>
</template>

<script>
import search from "./components/search";

export default {
  name: "App",
  components: {
    search
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.logo {
  width: 200px;
  height: 200px;
}
</style>
