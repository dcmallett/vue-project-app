<template>
  <ul>
      <ProjectResources 
        v-for="project in projectRes" 
        :key="project.id"
        :title="project.title"
        :link="project.link"
        :description="project.description"
      />
  </ul>
</template>

<script>
import ProjectResources from './ProjectResources.vue';
export default {
    ProjectResources
}
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