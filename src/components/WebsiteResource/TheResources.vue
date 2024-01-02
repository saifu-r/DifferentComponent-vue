<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-websites')" :mode="storedButtonMode">
      Stored Websites
    </base-button>
    <base-button @click="setSelectedTab('add-websites')" :mode="addStoredButtonMode"
      >Add Websites</base-button
    >
  </base-card>

  <component :is="selectedTab"></component>
</template>

<script lang="ts">
import { ref, provide, computed } from "vue";
import StoredWebsites from "./StoredWebsites.vue";
import AddWebsites from "./AddWebsites.vue";
export default {
  components: { StoredWebsites, AddWebsites },

  setup() {
    const selectedTab = ref("stored-websites");

    const setSelectedTab = (tab: string) => {
      selectedTab.value = tab;
    };

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

    const storedButtonMode= computed (()=>{
        return selectedTab.value === 'stored-websites' ? null : 'flat'
    })
    const addStoredButtonMode= computed(()=>{
         return selectedTab.value === 'add-websites' ? null : 'flat'
    })

    provide("websites", websites);

    return { selectedTab, setSelectedTab, storedButtonMode, addStoredButtonMode };
  },
};
</script>