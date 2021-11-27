<template>
  <div class="categories-wrapper">
    <a>Fast Cars</a>
    <a>EV's</a>
    <a>Prototypes</a>
    <a>Infotainment systems</a>
  </div>
</template>

<script>
export default {
  name: "Categories",
};
</script>

<style lang="scss" scoped>
.categories-wrapper {
  margin-bottom: 16px;
  a {
    margin-right: 20px;
    font-family: "Josefin Sans";
    cursor: pointer;
    &:hover {
      color: darkcyan;
    }
  }
}
</style>
