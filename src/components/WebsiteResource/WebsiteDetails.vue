
import { mergeProps } from 'vue';
<template>
  <li>
    <base-card>
      <header>
        <h3>{{ title }}</h3>
        <base-button mode="flat" @click="handleRemoveWebsite(id)">Delete</base-button>
      </header>

      <p>{{ description }}</p>
      <nav><a :href="link">View Website</a></nav>
    </base-card>
  </li>
</template>

<script lang="ts">
import { defineComponent, inject, ref } from "vue";


export default defineComponent({

  inject: ['removeWebsite'],
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
  
  setup(props){
    const propId= ref(props.id)
    const removeWebsite= inject("removeWebsite")

    const handleRemoveWebsite= (id: number)=>{
      if(removeWebsite){
        removeWebsite(id)
      }
    }

   

    return {removeWebsite, propId, handleRemoveWebsite}
  }
});
</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>
