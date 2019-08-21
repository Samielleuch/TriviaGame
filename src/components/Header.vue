<template>
    <div>
        <v-toolbar color="teal darken-3" dark>
            <v-app-bar-nav-icon class="hidden-md-and-up" @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-spacer class="hidden-md-and-up"></v-spacer>
            <v-toolbar-title> Trivia Questions Game </v-toolbar-title>
            <v-spacer></v-spacer>
        </v-toolbar>
    </div>
</template>

<script>
    export default {
        name: "Header"
    }
</script>

<style scoped>

</style>