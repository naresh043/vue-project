<template>
    <base-card>
      <base-button @click="selectTab('stored-resources')"
        >Stored resources</base-button
      >
      <base-button @click="selectTab('add-resource')">Add resources</base-button>
    </base-card>
    <component :is="selectedTab"></component>
  </template>
  
  <script>
  import StoredResources from "./StoredResources.vue";
  import AddResource from "./AddResource.vue";
  
  export default {
    components: {
      StoredResources,
      AddResource
    },
    data() {
      return {
        selectedTab: "stored-resources",
        storedResources: [
          {
            id: 1,
            name: "Vue.js Guide",
            title: "Official Guide",
            description: "The official Vue.js documentation",
            link: "https://vuejs.org/guide/"
          },
          {
            id: 2,
            name: "Google Developers",
            title: "Web Fundamentals",
            description: "Google's Web Development Resources",
            link: "https://developers.google.com/web"
          }
        ]
      };
    },
    provide() {
      return {
        resources: this.storedResources
      };
    },
    methods: {
      selectTab(tab) {
        this.selectedTab = tab;
      }
    }
  };
  </script>