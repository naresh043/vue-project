<template>
  <the-header title="Remember me"></the-header>
  <div>
    <StoredResources :resource="storedResource"></StoredResources>
  </div>
</template>

<script>
import StoredResources from "./components/learning-resources/StoredResources.vue";
import TheHeader from "./components/layouts/TheHeder.vue";

export default {
  name: "App",
  data() {
    return {
      storedResource: [
        {
          id: 1,
          name: "Resource 1",
          title: "official resource",
          description:
            "The official Vue js Documentation Description of Resource 1",
          link: "https://vuejs.org/v2/guide/",
        },
        {
          id: 2,
          name: "Resource 2",
          title: "official Google Documentation",
          description:
            "The official Google Documentation Description of Resource 2",
          link: "https://developers.google.com/web/fundamentals/web-app-manifest/",
        },
      ],
    };
  },
  components: {
    StoredResources,
    TheHeader,
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.learning-resource {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 16px;
  margin: 8px 0;
  background-color: #f9f9f9;
  transition: box-shadow 0.3s ease;
}

.learning-resource:hover {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.learning-resource h3 {
  margin: 0;
  font-size: 1.5em;
  color: #2c3e50;
}

.learning-resource p {
  margin: 8px 0;
  color: #555;
}

.learning-resource a {
  color: #42b983;
  text-decoration: none;
}

.learning-resource a:hover {
  text-decoration: underline;
}
</style>
