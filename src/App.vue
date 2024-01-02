<template>
  <div>
    <website-details
      v-for="website in websites"
      :key="website.id"
      :title="website.title"
      :description="website.description"
      :link="website.link"    
    ></website-details>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import WebsiteDetails from "./components/WebsiteResource/WebsiteDetails.vue";

export default defineComponent({
  name: "App",
  components: {
    WebsiteDetails,
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
</style>
