<template>
  <div>
    <Toolbar v-on:search="searchEvent"></Toolbar>
    <div class="ma-10 pa-4">
      <v-row dense>
        <v-col v-for="col in computedCols" :key="col.index" :cols="12 / computedDivisionVal">
          <Card class="mb-6" v-for="album in col" :key="album.id" :album="album"></Card>
        </v-col>
      </v-row>
    </div>
  </div>
</template>

<script>
import Card from './card/Card.vue';
import Toolbar from './Toolbar.vue';
  export default {
  components: { Card, Toolbar },
    name: 'Main',
    data: () => ({
      albums: [
        {
          id: 1,
          type: "album",
          name:"Certified Lover Boy",
          artist:"Drake",
          coverArt:"https://i.scdn.co/image/ab67616d00001e02bd6587e9a32c161be8c71100",
          desc:"If I paid somebody to make an album that's so generically \"Drake\", this is what they would make.",
        },
        {
          id: 2,
          type: "album",
          name:"Donda",
          artist:"Kanye West",
          coverArt:"https://i.scdn.co/image/ab67616d00001e026ba1cffc9b2c5469503430b3",
          desc:"This is doesn't hold up in the slightest against previous West albums, and it's honestly upsetting considering how much this was hyped.",
        },
        {
          id: 3,
          type: "single",
          name:"I Love It (& Lil Pump)",
          artist:"Kanye West, Lil Pump",
          coverArt:"https://media.pitchfork.com/photos/5b92d9a13cb3cb2f70596b8a/1:1/w_500/I%20LOVE%20IT%20COVER%20ART.jpg",
          desc:"This is the best Minecraft mod I've ever seen in my life.",
        },
        {
          id: 4,
          type: "album",
          name:"Donda",
          artist:"Kanye West",
          coverArt:"https://i.scdn.co/image/ab67616d00001e026ba1cffc9b2c5469503430b3",
          desc:"This is doesn't hold up in the slightest against previous West albums, and it's honestly upsetting considering how much this was hyped.",
        },
        {
          id: 5,
          type: "album",
          name:"Donda",
          artist:"Kanye West",
          coverArt:"https://i.scdn.co/image/ab67616d00001e026ba1cffc9b2c5469503430b3",
          desc:"This is doesn't hold up in the slightest against previous West albums, and it's honestly upsetting considering how much this was hyped.",
        },
        {
          id: 6,
          type: "album",
          name:"Certified Lover Boy",
          artist:"Drake",
          coverArt:"https://i.scdn.co/image/ab67616d00001e02bd6587e9a32c161be8c71100",
          desc:"If I paid somebody to make an album that's so generically \"Drake\", this is what they would make.",
        },
        {
          id: 7,
          type: "album",
          name:"Donda",
          artist:"Kanye West",
          coverArt:"https://i.scdn.co/image/ab67616d00001e026ba1cffc9b2c5469503430b3",
          desc:"This is doesn't hold up in the slightest against previous West albums, and it's honestly upsetting considering how much this was hyped.",
        },
      ],
      filteredAlbums: [],
    }),
    computed:{
      computedDivisionVal() {
        let bp = this.$vuetify.breakpoint.name;
        
        switch (bp) {
          case 'xs': return 1;
          case 'sm': return 2;
          case 'md': return 3;
          case 'lg': return 4;
          case 'xl': return 4;
          default: return 0;
        }
      },
      computedCols() {
        let cols = [[],[],[],[]];
        let listToUse = this.filteredAlbums.length > 0 ? this.filteredAlbums : this.albums;
        for (let index = 0; index < listToUse.length; index++) {
          cols[index % this.computedDivisionVal].push(listToUse[index]);
        }
        return cols;
      },
    },
    methods: {
      searchEvent(searchValue) {
        this.filteredAlbums = this.albums.filter(obj => Object.keys(obj).some(key => obj[key].includes(searchValue)));
        console.dir(this.filteredAlbums);
      }
    },
    mounted() {
      
    },
  };
</script>