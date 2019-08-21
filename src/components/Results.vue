<template>
    <v-card>
         <v-card-title>
             Congrats you scored  {{score}} / {{total}}
         </v-card-title>
        <v-progress-circular
                :value="60"
                color="brown"
        ></v-progress-circular>
    </v-card>
</template>

<script>
    export default {
        name: "Results"
        ,
        props :{
            score : Object ,
            total : Object
        }
    }
</script>

<style scoped>

</style>