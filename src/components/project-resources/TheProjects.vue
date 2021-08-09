<template>
<!-- this mimics the TheResources component -->
    <base-card>
        <base-button @click="setSelectedTab('project-resources')">Project Resources</base-button>
        <base-button @click="setSelectedTab('add-project')">Add Projects</base-button>
    </base-card>

    
    <!-- 
        NOTE: you need to make sure you use the component element when you want to display tabs else nothing will render
    -->
     <keep-alive>
            <component :is="selectedTab"></component>
    </keep-alive>
</template>

<script>
import AddProject from './AddProject.vue';
import ProjectResources from './ProjectResources.vue';

export default {
    components: {
        AddProject,
        ProjectResources
    },
    data() {
        return {
            selectedTab: 'project-resources',
            projectResources: [
                {
                    id: 'official-guide',
                    title: 'Official-Guide',
                    link: 'https://v3.vuejs.org/', 
                    description: 'This is the offical VueJs Guide',
                },
                {
                    id: 'twitch',
                    title: 'Twitch',
                    link: 'twitch.tv',
                    description: 'This is a live streaming platform',
                },
            ]
        }
    },
    provide() {
        return {
            projects: this.projectResources,
            addProject: this.addProject,
            //left side i.e
            //delete project can be anyname
            //this.deleteProject for example needs to match the method we create here.
            deleteProject: this.deleteProject
        }
    },
    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab;
        },
        addProject(title, url, description) {
            const newProject = {
                id: new Date().toISOString(),
                title: title,
                link: url,
                description: description
            };
            this.projectResources.unshift(newProject);
            this.selectedTab = ('project-resources');
        },

        deleteProject(projId) {
            const projIndex = this.projectResources.findIndex(project => project.id === projId)
            this.projectResources.splice(projIndex, 1);
        }
    }
}
</script>

<style scoped>

</style>