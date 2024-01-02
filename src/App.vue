<template>
  <the-header title="About Me"></the-header>
  <stored-websites :websites="websites"></stored-websites>

  
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StoredWebsites from "./components/WebsiteResource/StoredWebsites.vue";
import TheHeader from "./components/layouts/TheHeader.vue";


export default defineComponent({
  name: "App",
  components: {
    StoredWebsites, TheHeader
  },
  setup() {
    const websites = [
      {
        id: 1,
        title: "Github",
        description:
          "GitHub is a code hosting platform for version control and collaboration",
        link: "https://github.com/saifu-r",
      },
      {
        id: 2,
        title: "LinkedIn",
        description:
          "LinkedIn is the world's largest professional network on the internet.",
        link: "https://www.linkedin.com/in/saifur-rahman-597793274/",
      },
    ];

    return {websites}
  },
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
