<template>
    <header>
        <h2>{{ title }}</h2>
    </header>
</template>

<script>
export default {
    props: {
        title: {
            type: String,
            requried: true
        }
    }
}
</script>