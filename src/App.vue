<template>
  <app-container></app-container>
</template>


<script lang="ts">
import Vue from "vue";
import appContainer from "./components/appContainer.vue";
export default Vue.extend({
  name: "App",

  components: {
    appContainer,
  },
});
</script>


<style>
html {
  background-color: #eee;
}
</style>
