<template>
  <base-card>
    <base-button
      @click="selectTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored resources</base-button
    >
    <base-button @click="selectTab('add-resource')" :mode="addResButtonMode"
      >Add resources</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from "./StoredResources.vue";
import AddResource from "./AddResource.vue";

export default {
  components: {
    StoredResources,
    AddResource,
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
          link: "https://vuejs.org/guide/",
        },
        {
          id: 2,
          name: "Google Developers",
          title: "Web Fundamentals",
          description: "Google's Web Development Resources",
          link: "https://developers.google.com/web",
        },
      ],
    };
  },
  provide() {
    return {
      resources: this.storedResources,
      addResource: this.addResource,
      deleteResource: this.removeResource,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === "stored-resources" ? null : "flat";
    },
    addResButtonMode() {
      return this.selectedTab === "add-resource" ? null : "flat";
    },
  },
  methods: {
    selectTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, link) {
      const newRes = {
        id: new Date().toISOString(),
        name: title,
        title: title,
        description: description,
        link: link,
      };
      this.storedResources.unshift(newRes);
    },
    removeResource(id) {
        // this.storedResources = this.storedResources.filter(
        //   (res) => res.id !== id
        // );
        const index = this.storedResources.findIndex((res) => res.id === id);
        this.storedResources.splice(index, 1);
      }
  },
};
</script>
