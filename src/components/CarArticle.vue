<template>
  <div class="article">
    <article class="inner-wrapper-article">
      <figure class="figure">
        <img
          v-if="showImage"
          :alt="altTxt"
          :height="imageHeight + 'px'"
          :src="localhost + imageSource"
          class="image skeleton"
        />
      </figure>
      <span class="inner-wrapper-article_text-content">
        <h1>{{ article.Title }}</h1>
        <h2>{{ article.Lead }}</h2>
        <p>{{ article.Body }}</p>
      </span>
    </article>
  </div>
</template>

<script>
export default {
  name: "CarArticle",
  data() {
    return {
      altTxt: this.article.image.alternativeText,
      imageSource: this.article.image.url,
      localhost: "http://localhost:0000",
    };
  },
  computed: {},
  props: {
    showImage: {
      type: Boolean,
    },
    article: {
      type: Object,
    },
    imageHeight: {
      type: Number,
    },
  },
};
</script>

<style lang="scss" scoped>
* {
  color: black;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.article {
  text-align: left;
  margin: 9px;
  border-bottom: 1px solid #e8e8e8;
  cursor: pointer;
  background: white;
  margin-bottom: 24px;

  .inner-wrapper-article {
    display: grid;
    min-height: 350px;

    .inner-wrapper-article_text-content {
      padding: 12px;
    }

    p {
      margin-bottom: 20px;
      max-height: 80px;
      overflow: hidden;
    }

    .figure {
      height: fit-content;

      .image {
        width: 100%;
        max-height: 550px;
        object-fit: cover;
        min-height: 255px;
        margin-bottom: 13px;
        // order: -1;
        &.skeleton {
          animation: skeleton-loading 1s linear 10 alternate;
        }

        @media screen and (max-width: 768px) {
          width: 100%;
          min-height: 250px;
        }
      }
    }
  }
}

@keyframes skeleton-loading {
  0% {
    background-color: rgb(247, 247, 247);
  }
  100% {
    background-color: rgb(67, 173, 187);
  }
}
</style>
