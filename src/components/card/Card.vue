<template>
  <v-hover v-slot="{ hover }">
    <v-card color="#FAD2CC" max-width="400" class="pb-6">

      <v-img :aspect-ratio="hover ? 1/1 : 16/9" :src="album.coverArt">
        <v-overlay absolute v-if="!hover" opacity="0.25" z-index="-1"></v-overlay>
      </v-img>

      <div class="mx-6 mt-6">
        <v-card-title class="pa-0">
          {{album.name}}
          <v-spacer></v-spacer>

          <v-tooltip left v-if="album.type === 'album'">
            <template v-slot:activator="{ on }">
              <v-icon v-on="on">mdi-album</v-icon>
            </template>
            <span>Album</span>
          </v-tooltip>

          <v-tooltip left v-if="album.type === 'single'">
            <template v-slot:activator="{ on }">
              <v-icon v-on="on">mdi-star-circle</v-icon>
            </template>
            <span>Single</span>
          </v-tooltip>

        </v-card-title>
        <v-card-subtitle class="pa-0 font-italic">{{album.artist}}</v-card-subtitle>
        <v-divider class="mt-2 mb-2"></v-divider>
        <span>{{album.desc}}</span>
      </div>

      <!-- <v-card-actions class="pt-0">
        <v-spacer></v-spacer>
        <v-btn text outlined>
          go to album review
        </v-btn>
      </v-card-actions> -->
    </v-card>
  </v-hover>
</template>

<script>
  export default {
    name: 'Card',
    props: {
      album: {
        type: Object,
        default: function () {
          return {}
        }
      }
    },
    components: {},
    data: function() {
      return {
      }
    },
    methods: {
      event() {

      },
    },
    mounted() {

    }
  }
</script>

<style>
.zoom {
  padding: 50px;
  background-color: green;
  transition: transform .2s; /* Animation */
  margin: 0 auto;
}

.zoom:hover {
  transform: scale(1.5); /* (150% zoom)*/
}

.item-fade {
  background: black;
  opacity: 0.8;
  transition: opacity .25s ease-in-out;
  -moz-transition: opacity .25s ease-in-out;
  -webkit-transition: opacity .25s ease-in-out;
}
</style>