<template>
  <div class="disc p-3">
      <div class="p-3 text-center">
         <img class="img-fluid mb-3" :src="disc.poster" :alt="disc.name">
         <h5> {{disc.title}} </h5>
         <h6> {{ disc.year }} </h6>
      </div>
  </div>
</template>

<script>
export default {
    name:'Disc',
   props:{
       disc: Object
   }
}
</script>

<style lang="scss" scoped>
    .disc{
        flex-basis: calc(100% / 5);
        min-height: 300px;
        div{
            background-color: #2E3A46;
            height: 100%;
            h6{
                color: #7D7977;
            }
        }
    }
</style>