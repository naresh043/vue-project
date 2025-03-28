<template>
  <ul>
    <LearningResources
      v-for="res in resource"
      :key="res.id"
      :name="res.name"
      :title="res.title"
      :description="res.description"
      :link="res.link"
    />
  </ul>
</template>

<script>
import LearningResources from "./LerningResources.vue";

export default {
  props: ["resource"],
  components: {
    LearningResources,
  },
};
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
