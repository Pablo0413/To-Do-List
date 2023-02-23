<template>
    <div class="container mt-2" v-if="notes.length != 0">
        <div v-for="(note, index) in notes" :key="index">
            <b-card :title="note.subject" class="mb-2" id="firstcard">
                <b-card-text>{{ note.description }}</b-card-text>

                <b-button variant="outline-secondary" class="mr-2" @click="edit(index)">Edit</b-button>
                <b-button variant="outline-danger" class="mr-2" @click="remove(note, index)">Delete</b-button>
            </b-card>
        </div>

        <b-modal ref="modalRemove" hide-footer title="Delete the note">
            <div class="d-block text-center">
                <p>Do you really want to delete this note</p>
                <p>Note: {{ noteSelected.subject }}</p>
            </div>
            <div class="mt-3 d-flex justify-content-end">
                <b-button variant="outline-secondary" class="mr-2" @click="hideModal">Cancel</b-button>
                <b-button variant="outline-danger" class="mr-2" @click="confirmRemoveNote">Delete</b-button>
            </div>
        </b-modal>
    </div>
    <div class="container mt-2 showcase" v-else>
        <b-card class="mb-2" id="firstcard">
            <b-card-text>Well, you haven't created any notes yet..</b-card-text>
            <b-card-text>Let's create one?</b-card-text>
            <b-button variant="outline-danger" class="mr-2" to="/form">Just click here!</b-button>
        </b-card>
    </div>
</template>

<script>
export default {
    name: "List",

    data() {
        return {
            notes: [],
            noteSelected: []
        }
    },
    created() {
        this.notes = (localStorage.getItem("notes")) ? JSON.parse(localStorage.getItem("notes")) : [];
    },

    methods: {
        edit(index) {
            this.$router.push({ name: "form", params: { index } });
        },

        remove(note, index) {
            this.noteSelected = note;
            this.noteSelected.index = index;
            this.$refs.modalRemove.show();
        },

        hideModal() {
            this.$refs.modalRemove.hide();
        },

        confirmRemoveNote() {
            this.notes.splice(this.noteSelected.index, 1);
            localStorage.setItem("notes", JSON.stringify(this.notes));
            this.hideModal();
        }
    }
}
</script>

<style>
#firstcard {
    background-color: rgba(17, 44, 39, 1);
    border-radius: 20px;
    color: rgb(219, 209, 209);
    box-shadow: -1px 1px 11px 1px rgba(0, 0, 0, 0.36);
    -webkit-box-shadow: -1px 1px 11px 1px rgba(0, 0, 0, 0.36);
}

.showcase {
    height: calc(100vh - 64px) !important;
    width: 100vh !important;
    display: flex !important;
    justify-content: flex-start !important;
    align-items: center !important;
}
</style>