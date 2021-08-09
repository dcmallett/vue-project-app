<template>
    <!-- this is the learning resources-->
 <li>
        <base-card>
            <header>
                <h3>{{ title }}</h3>
                <base-button @click="deleteProject(id)">Delete Project</base-button>
            </header>
            <p>{{ description }}</p>
            <nav>
                <a :href="link">View Project</a>
            </nav>
        </base-card>
    </li>
</template>

<script>
export default {
    props: ['id', 'title', 'description', 'link'],
    inject: ['deleteProject']
}
</script>

<style scoped>
li {
    margin: auto;
    max-width: 40rem;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

h3 {
    font-size: 1.25rem;
    margin: 0.5rem 0;    
}

p {
    margin: 0.5rem 0;
}

a {
    text-decoration: none;
    color: #c35c00;
}

a:hover,
a:active {
    color: #c89300;
}
</style>