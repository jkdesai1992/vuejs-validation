<template>
  <div id="app">
    <img width="25%" src="./assets/logo.png">
    <ValidationForm/>
  </div>
</template>

<script>
import ValidationForm from "./components/ValidationForm";

export default {
  name: "App",
  components: {
    ValidationForm
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
