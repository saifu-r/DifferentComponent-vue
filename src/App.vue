<template>
  <the-header title="About Me"></the-header>
  <the-resources></the-resources>
  

  
</template>

<script lang="ts">
import { defineComponent} from "vue";
// import StoredWebsites from "./components/WebsiteResource/StoredWebsites.vue";
import TheHeader from "./components/layouts/TheHeader.vue";
import TheResources from "./components/WebsiteResource/TheResources.vue";



export default defineComponent({
  name: "App",
  components: {
     TheHeader, TheResources
  }
  
});
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
