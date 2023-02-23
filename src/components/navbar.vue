<template>
    <b-navbar toggleable="lg" class="navbar" type="dark">
        <b-navbar-brand class="title" to="/">To Do List</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
            <b-navbar-nav class="flex">
                <b-nav-item to="/list">
                    Notes
                </b-nav-item>
                <b-nav-item to="/form">Add new Note</b-nav-item>
            </b-navbar-nav>

        </b-collapse>
    </b-navbar>
</template>

<script>
export default {
    name: "addNoteForm",
}
</script>

<style>
.title {
    font-weight: 600;
}

.navbar {
    background-color: rgba(17, 44, 39, 1);
    box-shadow: 0px 1px 5px -2px rgba(0, 0, 0, 0.45);
    -webkit-box-shadow: 0px 1px 5px -2px rgba(0, 0, 0, 0.45);
}
</style>