<template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>
    <a :href=link>Click</a>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    id: {
      type: Number,
      required: false,
    },
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
    link: {
      type: String,
      required: true,
    },
  },
  
});
</script>

<style scoped>
</style>
