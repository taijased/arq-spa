
<template>
  <div class="wrapper">
    <header>
     <app-header></app-header>
    </header>
    <main>
      <custom-swiper></custom-swiper>
    </main>
  </div>
</template>

<script>
import AppHeader from "./Header";
import CustomSwiper from "./CustomSwiper";

export default {
  components: {
    AppHeader,
    CustomSwiper
  }
};
</script>

<style lang="less">
.wrapper {
  display: grid;
  height: 100vh;
  grid-template-rows: 15vh 85vh;
  grid-template-columns: 50vw 50vw;
  overflow: hidden;
  header {
    grid-row: 1;
    grid-column: ~"1 / 3";
    display: flex;
    flex-direction: row;
    align-items: center;
    background: rgba(0, 0, 0, 0.0);
  }
  main {
    grid-row: 2;
    grid-column:  ~"1 / 3";
    .container > .left-bar{
      height: 75vh;
    }
  }
}
</style>
