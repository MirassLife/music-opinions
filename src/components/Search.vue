<template>
  <div class="ma-4 mt-8">
    <v-text-field dense single-line
      v-model="searchValue"
      color="black"
      label="Search..."
      append-icon="mdi-magnify"
    ></v-text-field>
  </div>
</template>

<script>
  export default {
    name: 'Search',
    components: {},
    data: function() {
      return {
        searchValue: '',
      }
    },
    methods: {
      event() {

      },
    },
    watch: {
      searchValue: function(newV) {
        this.$emit('search', String(newV).toLowerCase);
        console.log('emit');
        console.log(this.searchValue);
      },
    },
    mounted() {

    }
  }
</script>