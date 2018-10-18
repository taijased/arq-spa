<template>
  <!-- <div id="app"> -->
    <!-- <app-index></app-index> -->
    <router-view/>
  <!-- </div> -->
</template>

<script>
// import AppIndex from "./components/Index";

export default {
  // components: {
  //   AppIndex
  // }
};
</script>

<style>
@import url('../src/styles/font.less');
* {
  margin: 0;
  padding: 0;
}
body {
  height: 100%;
  width: 100%;
  position: relative;
  overflow: hidden;
}

</style>
