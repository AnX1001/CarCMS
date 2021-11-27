<template>
  <div class="app">
    <GridLayout>
      <template v-slot:main-article>
        <!-- clickable main feature article ie. article with largest image -->
        <router-link to="/MainFeatureArticle" tag="div"
          ><CarArticle
            class="feature-article"
            v-for="(article, index) in CarArticles.slice(0, 1)"
            :key="index"
            :article="article"
            showImage
        /></router-link>
      </template>

      <!-- small articles below main feature article -->
      <template v-slot:side-article-below-feature>
        <div
          class="wrapper"
          v-for="(article, index) in CarArticles.slice(2)"
          :key="index"
        >
          <CarArticle
            showImage
            :imageHeight="imageHeight"
            :article="article"
            class="side-article"
          />
        </div>
      </template>

      <!-- side articles on the left side, i.e. left to the main feature article -->
      <template v-slot:side-article-first>
        <div
          class="wrapper"
          v-for="(article, index) in CarArticles.slice(0)"
          :key="index"
        >
          <CarArticle
            showImage
            :imageHeight="imageHeight"
            :article="article"
            class="side-article"
          />
        </div>
      </template>

      <!-- side articles on right hand side of the main feature article -->
      <template v-slot:side-article-second>
        <div
          class="wrapper"
          v-for="(article, index) in CarArticles.slice(0)"
          :key="index"
        >
          <CarArticle
            showImage
            :imageHeight="imageHeight"
            :article="article"
            class="side-article"
          />
        </div>
      </template>

      <!-- final right hand side small article -->
      <template v-slot:side-article-third>
        <div
          class="wrapper"
          v-for="(article, index) in CarArticles.slice(3)"
          :key="index"
        >
          <CarArticle
            showImage
            :imageHeight="imageHeight"
            :article="article"
            class="side-article"
          />
        </div>
      </template>
    </GridLayout>
  </div>
</template>

<script>
import GridLayout from "../components/GridLayout";
import CarArticle from "../components/CarArticle";
export default {
  name: "Home",
  components: { GridLayout, CarArticle },
  data() {
    return {
      CarArticles: [],
      imageHeight: 150,
    };
  },
  methods: {
    async fetchArticles() {
      try {
        let networkRequest = await fetch("http://localhost:0000/collection");
        let parsedToJSON = await networkRequest.json();
        this.CarArticles = parsedToJSON;
      } catch (error) {
        console.log(error);
      }
    },
  },
  mounted() {
    this.fetchArticles();
  },
};
</script>

<style lang="scss">
#app {
  font-family: serif, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

h1 {
  font-family: "Josefin Sans", cursive;
  text-align: center;
  font-size: 35px;
}
.line {
  height: 1px;
  border: 0;
  border-top: 1px solid #ccc;
  margin: 1em 0;
  padding: 0;
}

.grid-layout-wrapper {
  .side-article {
    padding: 11px;
    display: flex;
  }
  .feature-article {
    h1 {
      font-size: 40px;
    }
  }
}
</style>
