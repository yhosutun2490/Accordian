<template>
<container class="container">
  <header class="header"></header>
  <FaqCardVue/>
</container>
</template>

<script setup>
import FaqCardVue from "./components/FaqCard.vue";

</script>

<style scoped>
.container {
  width: 100%;
  height: 100%;
  background-color: #F8EEFF;
  margin: 0;
  position: relative;
  display: flex;
}
.header {
  background: url(./assets/images/background-pattern-desktop.svg);
  width: 100%;
  height: 35%;
  background-size: auto;
}


</style>
