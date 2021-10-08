<template>
    <v-toolbar elevation="3">
        <v-row style="width: 100%" justify="center" align="center">
          <v-col align="center">
            <span>BAD MUSIC OPINIONS</span>
          </v-col>
          <v-spacer></v-spacer>
          <v-col align="center">
            <Search v-on:search="searchEvent"></Search>
          </v-col>
        </v-row>
      </v-toolbar>	
</template>

<script>
import Search from './Search.vue'
  export default {
    name: 'Toolbar',
    components: {Search},
    data: function() {
      return {
      }
    },
    methods: {
      searchEvent(val) {
        this.$emit('search', val);
      },
    },
    mounted() {

    }
  }
</script>

<style lang="scss">
  @import '../styles/variables.sass';  
  .v-toolbar {
    font-family: $body-title-family, sans-serif !important;
    font-size: 2em !important;
  }
</style>