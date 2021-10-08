<template>
  <v-app id="app">
    <v-card color="#edf6ff" flat height="100%">
      <span class="bg"></span>
    
      <Main></Main>

    </v-card>
  </v-app>
</template>

<script>
import Main from './components/Main.vue';

export default {
  components: { Main },
  name: 'App',
  data: () => ({
  }),
};
</script>

<style lang="scss">
  @import './styles/variables.sass';  
  #app {
    color: #edf6ff;
  }
  .v-application {
    font-family: $body-font-family, sans-serif !important;
  }
  html { 
    overflow-y: auto 
  }
</style>