<template>
  <TheHeader :title="'Vue Project Planner'" />
  <TheProjects />
</template>

<script>
import TheHeader from './components/layout/TheHeader.vue';
import TheProjects from './components/project-resources/TheProjects.vue'

export default {
  name: 'App',
  components: {
    TheHeader,
    TheProjects
    
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
