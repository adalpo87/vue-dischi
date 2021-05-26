<template>
<main class="container mt-5">
    <div class="d-flex flex-wrap">
        <Disc 
          v-for="(disc,index) in filterDiscs" :key="index" :disc="disc"/>
    </div>
    
</main>
</template>

<script>
import axios from 'axios';
import Disc from '@/components/Disc.vue'

export default {
    name: 'Main',
    components:{
        Disc
    },
    computed:{
        /* questa funzione mi permette poi di resettare ogni volta la lista e in base alla chiamata che faccio di filtrare */
        /* ultimo passaggio definiamo cosa vedere */
        filterDiscs(){
            if(this.genreToSearch === ''){
                return this.musicList;
            }
            return this.musicList.filter(item => item.genre === this.genreToSearch);
        }
    },
    data(){
        return{
            musicList:[],
            genreList:[],
        }
    },
    props:{
        genreToSearch: String,
    },
    created(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(res=> {
            this.musicList = res.data.response;
            this.musicList.forEach(disc => {
                /* condizione per non far inserire doppioni */
                if(!this.genreList.includes(disc.genre)){
                    this.genreList.push(disc.genre);
                }
            });
            /* devo mandare i dati ad app tramite un emit */
            this.$emit('onGenreList', this.genreList)
                    /* il primo dato è il nome che trasmetto e cha fa da riferimento, il secondo è cosa sto trasmettendo */
            /* ora sto trasmettendo l evento */
            console.log(this.genreList);
        })
        .catch(err=> {
            console.log(err)
        })
    }
}
</script>

<style lang="scss" scoped>

</style>