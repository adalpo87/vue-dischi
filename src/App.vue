<template>
  <div id="app">
    <!-- ora il dato lo spediamo con una props al header -->
    <Header :genreList="genreList"
            @startSearch="startSearch" />

    <!-- qui ricevio il dato -->
    <Main 
          :genreToSearch="genreToSearch"
          @onGenreList="getGenreList"
        />

  </div>
  
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
   /* quando si riceve un dato, bisogna sempre salvarlo */
  data(){
    return{
      genreList:[],
      genreToSearch: ''
    }
  },
  methods:{
    getGenreList(genreList){
        /* ricevo i dati e li salvo in genreList */
        this.genreList = genreList;
        console.log('---->',genreList)
    },   /* la funzione mi richiama il dato che mi interessa, in questo caso genreList che si trova in main */
    startSearch(genreToSearch){
      this.genreToSearch = genreToSearch;
    }
}}
</script>
<style lang="scss">

@import '@/assets/style/general.scss';

</style>
