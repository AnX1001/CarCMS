<template>
  <div class="grid-layout">
    <div class="side-articles">
      <CarArticle
        class="side-article"
        v-for="(article, index) in CarArticles.slice(0, 2)"
        :key="index"
        :article="article"
      />
    </div>
    <CarArticle
      v-for="(article, index) in CarArticles.slice(0, 1)"
      :key="index"
      :article="article"
      showImage
      class="feature-article"
    />

    <GeoAds class="ads" />
  </div>
</template>

<script>
import CarArticle from "../components/CarArticle";
import GeoAds from "../components/GeoAds";
export default {
  name: "MainFeatureArticle",
  components: { CarArticle, GeoAds },
  data() {
    return {
      CarArticles: [],
    };
  },
  async mounted() {
    try {
      fetch("http://localhost:0000/collection", {
        method: "GET",
        headers: { "Content-Type": "application/json" },
      })
        .then((response) => response.json())
        .then((data) => (this.CarArticles = data));
    } catch (error) {
      console.log(error);
    }
  },
};
</script>

<style lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.grid-layout {
  height: fit-content;
  width: 100%;
  background: gainsboro;

  display: grid;
  grid-template-columns: 20% 60% 20%;

  @media screen and (max-width: 768px) {
    grid-template-columns: 1fr;
  }

  .ads {
    height: 540px;
    background: white;
    margin: 16px;
    padding: 16px;
  }

  .side-articles {
    padding: 11px;

    .side-article {
      min-height: 150px;
      margin-bottom: 15px;
      background: white;
    }
  }

  .feature-article {
    width: 100%;
    margin: 20px 0;

    background: white;
    height: fit-content;
    @media screen and (max-width: 768px) {
      order: -1;
    }
  }
}
</style>
