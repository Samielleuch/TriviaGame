<template>
  <v-app>
    <Header/>
    <v-content >
      <v-container fluid fill-height class="background" >
        <QuestionBox/>
      </v-container>
    </v-content>
    <v-footer
            absolute
            class="font-weight-medium"
    >
      <v-col
              class="text-center"
              cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Sami Elleuch Inc </strong>
      </v-col>
    </v-footer>
  </v-app>
</template>

<script>
  import Header from "./components/Header";
  import QuestionBox from "./components/QuestionBox";
  import Results from "./components/Results";

  export default {
    name: 'App',
    components: {
      QuestionBox,
      Header,
      Results ,
    },
    data: () => ({
      questions :[] ,
    })
  };
</script>
<style scoped>
  .background {
    background: url('https://images.unsplash.com/photo-1492892132812-a00a8b245c45?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80');
    background-size: cover;
    width: 100%;
    height: 100%;
  }
</style>
