<template>
  <Jueguito/>
</template>

<script>
import Jueguito from "./pages/JuegoPage.vue";
export default {
  name: "App",
  components: {
    Jueguito
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
