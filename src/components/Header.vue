<script>  
  import { store } from '../data/store'
  export default {
    data(){
      return{
        store,
        characterToSearch: '',
        statusToSearch: 'Select status',
        speciesToSearch: '',
      }
    },

    methods:{
      reset(){
        this.characterToSearch = '';
        this.statusToSearch = 'Alive';
        this.speciesToSearch = ''
        this.startSearch();
      },

      startSearch(){
        if (this.characterToSearch || this.statusToSearch || this.speciesToSearch){
          this.store.queryParams = {
            name: this.characterToSearch,
            status: this.statusToSearch,
            species: this.speciesToSearch
          }
          this.$emit('startSearch')
          console.log(this.store.queryParams);
        }else{
          this.store.queryParams = {};
          this.$emit('startSearch')
        }

      },
    }
  }
</script>


<template>
  <div class="text-center my-3 container">
    <h1 class="text-white">{{ store.mainTitle }}</h1>
    <div class="d-flex my-5 justify-content-center">

      <input v-model.trim="characterToSearch" @keyup.enter="startSearch" class="form-control w-25"
        id="exampleDataList" placeholder="Type to search a name...">

      <datalist id="datalistOptions">
        <option v-for="(character, index) in this.store.characterList" :key="index" :value="character"></option>
      </datalist>

      <select v-model.trim="statusToSearch" @change="startSearch" class="form-select mx-3 w-25">
        <option selected>Select status</option>
        <option value="Alive">Alive</option>
        <option value="Dead">Dead</option>
        <option value="Unknown">Unknown</option>
      </select>

      <input v-model.trim="speciesToSearch" @keyup.enter="startSearch" class="form-control w-25"
        list="datalistOptionsSpecies" id="exampleDataList" placeholder="Type to search a species...">

      <datalist id="datalistOptionsSpecies">
        <option v-for="(character, index) in this.store.characterSpecies" :key="index" :value="character"></option>
      </datalist>

      <button @click="startSearch" class="btn btn-success mx-3">Search</button>
      <button @click="reset" class="btn btn-danger">Reset</button>
    </div>

  </div>
</template>


<style lang="scss" scoped>

</style>