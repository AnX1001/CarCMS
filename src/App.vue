<template>
  <div id="app">
    <h1 class="pageTitle">Driven</h1>
    <div id="nav">
      <router-link to="/"><a href="#">Return to homepage</a> </router-link>
    </div>
    <ArticleCategories />
    <router-view />
  </div>
</template>

<script>
import ArticleCategories from "./components/ArticleCategories.vue";
export default {
  name: "App",
  components: { ArticleCategories },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@300&display=swap");

#app {
  font-family: Josefin Sans, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  box-sizing: border-box;
  margin-top: 22px;
  padding: 0;

  .pageTitle {
    color: black;
    font-size: 5rem;
  }
}

#nav {
  a {
    font-weight: bold;
    color: black;
    text-decoration: none;

    &.router-link-exact-active {
      color: black;
      a:hover {
        color: darkcyan;
      }
    }
  }
}
</style>
