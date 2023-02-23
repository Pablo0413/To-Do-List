<template>
  <div class="container mt-2">
    <addNoteForm />
  </div>
</template>

<script>
import addNoteForm from '../components/addNoteForm.vue';

export default {
  name: "Form",

  components: {
    addNoteForm,
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
</style>