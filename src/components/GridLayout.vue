<template>
  <div class="grid">
    <div class="grid_side-article"><slot name="side-article-first"></slot></div>
    <div class="grid_main-article">
      <slot name="main-article"></slot>
      <slot name="side-article-below-feature"></slot>
    </div>
    <div class="side-article other-news">
      <slot name="side-article-second"></slot>
    </div>
    <div class="side-article opinions">
      <slot name="side-article-third"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "GridLayout",
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
p {
  font-family: "Josefin Sans";
}

.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  background: gainsboro;

  @media screen and (max-width: 1024px) {
    grid-template-columns: 1fr;
  }

  .grid_main-article {
    min-width: clamp(300px, 70vw, 760px);
    height: fit-content;
    padding: 12px;
  }
}
</style>
