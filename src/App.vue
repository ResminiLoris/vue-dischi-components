<template>
  <div id="app">
    <Header :genreList="genreList" @genreChange="genreChange"/>
    <Main :albums="filteredAlbums"/>
  </div>
</template>

<script>
import axios from "axios";
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data(){
    return{
      albums: [],
      selectedGenre:"All",
    }
  },
  computed:{
    //recupero generi musicali 
    genreList(){
      const genreList = [];
      this.albums.forEach(album => {
        if(!genreList.includes(album.genre))
        genreList.push(album.genre);
      });
      return genreList;
    },
    //ordino gli album per data
    orderedAlbums(){
      let orderedAlbums = this.albums.slice();
      return orderedAlbums.sort((a, b)=>{
        return a.year - b.year;
      });
    },
    //filtro album in base a genere selezionato
    filteredAlbums(){
      const albums = this.orderedAlbums;
      if(this.selectedGenre === 'All') return albums;
      return albums.filter((album)=>{
        return album.genre === this.selectedGenre;
      })
    },
    
    
  },
  methods:{
    //intercetto cambio genere (header)
    genreChange(selectedGenre){
      this.selectedGenre = selectedGenre;
    }
  },
  //recupero dati API
  created(){
    axios.get("https://flynn.boolean.careers/exercises/api/array/music").then((res)=>{
     console.log("LOG RES.DATA:",res.data.response)
     this.albums=(res.data.response);
    })
  }
}

</script>

<style lang="scss">
body{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background-color: #1E2D3B;
}
#app {
  .container {
  max-width: 1500px;
  margin: 0 auto;
  } 
}
</style>
