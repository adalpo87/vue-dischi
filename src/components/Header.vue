<template>
  <header class="d-flex justify-content-between align-items-center ps-5 pe-5">
     <div>
         <img src="@/assets/img/spotify-logo.png" alt="Spotify">
     </div>
     <div>
         <select 
         @change="$emit('startSearch', genreToSearch)"
         v-model="genreToSearch" 
         class="form-select">
         <!-- il v-model dentro select cattura l option e salva il dato in genreToSearch -->
             <option value="">Seleziona un genere</option>
             <option
              v-for="(genre, index) in genreList"
              :key="index"
              :value="genre"
              >{{ genre }}</option>
              <!-- il value deve essere il nostro genere -->
         </select>
     </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    props:{
        genreList: Array,
    },
    data(){
        return {
            genreToSearch:'',
        }
    },
    methods:{
    
    }
}
</script>

<style lang="scss" scoped>
    header{
        height: 100px;
        background-color: #2E3A46;
        div{
            img{
                height: 80px;
            }
        }
    }
</style>