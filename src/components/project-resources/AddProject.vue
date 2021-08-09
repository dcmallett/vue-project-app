<template>
  <h2>Add a new project</h2>

    <base-modal v-if="inputIsInvalid" title="Input is invalid" @closeModal="togglaModalDialog">
        <template #default>
            <p>Unfortunatley, at least one input field was invalid</p>
            <p>Please try again</p>
        </template>
        <template #actions>
            <base-button @click="togglaModalDialog">Close</base-button>
        </template>
    </base-modal>

  <base-card>
    <form @submit.prevent="AddProjectHandler">
        <div class="form-control">
            <label for="title">Project Title:</label>
            <input id="title" type="text" name="title" placeholder="Please add a project" ref="enteredProjTitle" />
        </div>
            <div class="form-control">
            <label for="link">Project Url:</label>
            <input id="link" type="text" name="link" placeholder="Please add a link to the project" ref="enteredProjLink" />
        </div>
        <div class="form-control">
            <label for="description">Project Description:</label>
            <textarea id="description" name="description" rows="3" placeholder="Please add a project description" ref="enteredProjDesc"></textarea>
        </div>
        <base-button type="submit">Add Project</base-button>
    </form>
  </base-card>
</template>

<script>
export default {
    data() {
        return {
            inputIsInvalid: false
        }
    },
    inject: ['addProject'],
    methods: {
        AddProjectHandler() {
            const projTitle = this.$refs.enteredProjTitle.value;
            const projLink = this.$refs.enteredProjLink.value;
            const projDesc = this.$refs.enteredProjDesc.value;
            
            //if any of these are equal to an empty string out modal popup will trigger and display.
            if (projTitle.trim() === '' || projLink.trim() === '' || projDesc.trim() === '') {
                this.inputIsInvalid = true;
                return;
            }

            this.addProject(projTitle, projLink, projDesc)
        },
        togglaModalDialog() {
            this.inputIsInvalid = false;
        }
    }
}
</script>

<style scoped>
h2 {
    text-align: center;
}

label {
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
}

input,
textarea {
    display: flex;
    width: 100%;
    font: inherit;
    padding: 0.15rem;
    border: 1px sold #ccc;
}

input:focus,
textarea:focus {
    outline: none;
    border-color: #3a0061;
    background-color: #f7ebff;
}

.form-control {
    margin: 1rem 0;
}
</style>