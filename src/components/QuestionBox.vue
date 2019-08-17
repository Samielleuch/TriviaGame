<template>
    <v-row justify="center">
        <v-col cols="5">
            <v-card>
                <v-system-bar color="teal darken-2"></v-system-bar>
                <v-toolbar color="teal" dark dense>
                    <v-toolbar-title>Question</v-toolbar-title>
                    <v-spacer></v-spacer>
                    <v-chip color="teal lighten-5" dark outlined ripple>Score: 0/0</v-chip>
                </v-toolbar>
                <v-card-text>
                    <v-row>
                        <v-col align="start">
                            <v-list shaped>
                                <v-list-item>
                                    <v-list-item-content>
                                        <v-list-item-title> Answers here Loop</v-list-item-title>
                                    </v-list-item-content>
                                </v-list-item>
                            </v-list>
                        </v-col>
                    </v-row>
                </v-card-text>
                <v-divider></v-divider>
                <v-row justify="center">
                    <v-col cols="2">
                        <v-btn outlined>Submit</v-btn>
                    </v-col>
                    <v-col cols="2">
                        <v-btn outlined>Next</v-btn>
                    </v-col>
                </v-row>


            </v-card>
        </v-col>
    </v-row>
</template>

<script>
    export default {
        name: "Question Box"
    }
</script>

<style scoped>

</style>