<template>
    <b-form>
        <b-form-group label="Title" label-for="subject" class="text">
            <b-form-input id="subject" v-model="addNoteForm.subject" type="text" placeholder="Example: watch anime" required
                autocomplete="off"></b-form-input>
        </b-form-group>

        <b-form-group label="Description" label-for="description" class="text">
            <b-form-textarea id="description" v-model="addNoteForm.description" type="text"
                placeholder="Example: watch 5 episodes of AoT per week" required autocomplete="off"></b-form-textarea>
        </b-form-group>

        <b-button type="submit" variant="outline-secondary" @click="saveNote">Save</b-button>
    </b-form>
</template>

<script>
export default {
    name: "addNoteForm",

    data() {
        return {
            addNoteForm: {
                subject: "",
                description: ""
            },
            methodSave: "new"
        }
    },

    created() {
        if (this.$route.params.index === 0 || this.$route.params.index !== undefined) {
            this.methodSave = "update";
            let notes = JSON.parse(localStorage.getItem("notes"));
            this.addNoteForm = notes[this.$route.params.index];
        }
    },

    methods: {
        saveNote() {
            if (this.methodSave === "update") {
                let notes = JSON.parse(localStorage.getItem("notes"));
                notes[this.$route.params.index] = this.addNoteForm;
                localStorage.setItem("notes", JSON.stringify(notes));
                this.$router.push({ name: "list" });
                return;
            }
            let notes = (localStorage.getItem("notes")) ? JSON.parse(localStorage.getItem("notes")) : [];
            notes.push(this.addNoteForm);
            localStorage.setItem("notes", JSON.stringify(notes));
            this.$router.push({ name: "list" });
        }
    }
}
</script>

<style>
.container {
    height: calc(100vh - 64px);
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    padding-top: 30px;
}

.text {
    color: rgb(63 127 129);
    font-weight: 600;
}

#description,
#subject {
    background-color: rgba(17, 44, 39, 1);
    border-radius: 7px;
    color: rgb(255, 255, 255);
    box-shadow: -1px 1px 11px 1px rgba(0, 0, 0, 0.36);
    -webkit-box-shadow: -1px 1px 11px 1px rgba(0, 0, 0, 0.36);
    border: none;
}
</style>
