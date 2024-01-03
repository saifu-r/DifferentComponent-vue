<template>
  <ul>
    <website-details
      v-for="website in websites"
      :key="website.id"
      :title="website.title"
      :description="website.description"
      :link="website.link"
    ></website-details>
  </ul>
</template>

<script lang="ts">
import { defineComponent, inject } from "vue";
import WebsiteDetails from "./WebsiteDetails.vue";

export default defineComponent({
  components: { WebsiteDetails },

  setup() {
    const websites = inject("websites");

    return { websites };
  },
});
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>
