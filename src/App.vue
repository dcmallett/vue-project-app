<template>
  <TheHeader :title="'Vue Project Planner'" />
  <add-project></add-project>
</template>

<script>
import TheHeader from './components/layout/TheHeader.vue';
import AddProject from './components/project-resources/AddProject.vue';

export default {
  name: 'App',
  components: {
    TheHeader,
    AddProject
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
    box-sizing: border-box;
}

html {
    font-family: 'Roboto', sans-serif;
}

body { 
    margin: 0;
}

</style>
