<script>
  import Card from './partial/Card.vue'
  import { store } from '../data/store';
  export default {
    components:{
      Card,
    },
    
    data(){
      return{
        store
      }
    }
  }
</script>


<template>
  <div class="container text-center my-3">
    <div
      v-if="this.store.cardsList.length > 0"
      class="row row-cols-2 d-flex justify-content-center">
      <Card 
        class="m-3"
        v-for="card in this.store.cardsList"
        :key="card.id"
        :name="card.name"
        :status="card.status"
        :species="card.species"
        :image="card.image"
      />
    </div>
    <h2 class="text-center" v-else-if="this.store.errorString.length > 0">{{ this.store.errorString }}</h2>
  </div>
</template>


<style lang="scss" scoped>

</style>