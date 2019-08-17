<template>
  <v-app>
    <Header/>
    <v-content>
      <v-container fluid>
        <QuestionBox/>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
  import Header from "./components/Header";
  import QuestionBox from "./components/QuestionBox";

  export default {
    name: 'App',
    components: {
      QuestionBox,
      Header,
    },
    data: () => ({
      //
    }),
  };
</script>
