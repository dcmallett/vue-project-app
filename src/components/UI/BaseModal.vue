<template>
    <div>
        <dialog open>
            <header>
                    <slot name="header">
                        <h2>{{ title }}</h2>
                    </slot>
            </header>
            <section>
                <!-- default slot main content of modal -->
                <slot></slot>
            </section>
            <menu>
                <slot name="actions">
                    <base-button @click="$emit('closeModal')">Close Modal</base-button>
                </slot>
            </menu>
        </dialog>
    </div>
</template>

<script>
export default {
    props: {
        title: {
            type: String,
            requried: true
        }
    },
    emits: ['closeModal']
}
</script>

<style scoped>
div {
    position: fixed;
    left: 0;
    top: 0;
    height: 100vh;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.75);
    z-index: 10;
}

dialog {
    position: fixed;
    top: 20vh;
    left: 10vh;
    width: 80%;
    z-index: 100;
    border-radius: 2rem;
    border: none;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.30);
    padding: 0;
    margin: 0;
    overflow: hidden;
}

header {
    background-color: #3a0061;
    color: white;
    padding: 1rem;
}

header h2 {
    margin: 0;
}

section {
    padding: 1rem;
}

menu {
    padding: 1rem;
    display: flex;
    justify-content: flex-end;
    margin: 0;
}

@media (min-width: 768px) {
    dialog {
        left: calc(50% - 20rem);
        width: 40rem;
    }
}
</style>