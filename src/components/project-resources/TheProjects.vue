<template>
<!-- this mimics the TheResources component -->
    <base-card>
        <base-button @click="setSelectedTab('project-resources')">Project Resources</base-button>
        <base-button @click="setSelectedTab('add-project')">Add Projects</base-button>
    </base-card>
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
            selectedTab: 'the-projects',
            projects: [
                {
                    id: 'official-guide',
                    title: 'Official-Guide',
                    description: 'This is the offical VueJs Guide',
                    link: 'https://v3.vuejs.org/'
                },
                {
                    id: 'twitch',
                    title: 'Twitch',
                    description: 'This is a live streaming platform',
                    link: 'twitch.tv'
                },
            ]
        }
    },
    provide() {
        return {
            projectRes: this.ProjectResources
        }
    },
    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab;
        },
        AddProject(title, url, description) {
            const newProject = {
                id: new Date().toISOString(),
                title: title,
                link: url,
                description: description
            };
            this.ProjectResources.unshift(newProject);
            this.selectedTab = ('project-resources');
        }
    }
}
</script>

<style scoped>

</style>