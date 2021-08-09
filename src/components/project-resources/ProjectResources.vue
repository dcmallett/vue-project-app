<template>
<!-- this is the storedResouces -->
    <ul>
        <ProjectArea 
            v-for="project in projects"
            :key="project.id"
            :id="project.id"
            :title="project.title"
            :link="project.link"
            :description="project.description"
        />
    </ul>
</template>

<script>
import ProjectArea from './ProjectArea.vue';
export default {
    components: {
        ProjectArea
    },
    inject: ['projects']
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