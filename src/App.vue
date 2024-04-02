<script>
  import axios from 'axios';
  import { store } from './data/store';
  import Header from './components/Header.vue';
  import Main from './components/Main.vue';
  import Footer from './components/Footer.vue';
  export default {
    data(){
      return{
        store,
      }
    },

    components:{
      Header,
      Main,
      Footer,
    },

    methods:{
      getApi(){
        this.store.errorString = '';
        axios.get(this.store.apiUrl, {
          params: store.queryParams
        })
      .then(result => {
        this.store.cardsList = result.data.results;
        console.log(this.store.cardsList);
      })
      .catch(error => {
        console.log(error);
        this.store.errorString = 'Character not found'
      })
      },

      getAllCharacter(){
        axios.get(this.store.characterUrl)
        .then(res => {
          console.log(res.data.results);
          this.store.characterList = res.data.results.map(item => item.name)
          console.log(this.store.characterList);
        })
      },

      getAllSpecies() {
        axios.get(this.store.apiUrl)
          .then(res => {
            console.log(res.data.results);
            this.store.characterSpecies = [...new Set(res.data.results.map(spec => spec.species))]
            console.log(this.store.characterSpecies);
          })
      },
    },

    mounted(){
      this.getApi()
      this.getAllCharacter()
      this.getAllSpecies()
    }
  }
</script>

<template>
  <div>
    <Header @startSearch="getApi" />
    <Main />
    <Footer />
  </div>
</template>

<style lang="scss">
  body {
    min-height: 100vh;
    background: linear-gradient(
      135deg,
      rgba(247, 67, 124, 1) 0%,
      rgba(252, 157, 154, 1) 10%,
      rgba(255, 221, 160, 1) 20%,
      rgba(155, 246, 255, 1) 30%,
      rgba(153, 204, 255, 1) 40%,
      rgba(144, 148, 194, 1) 50%,
      rgba(52, 78, 163, 1) 60%,
      rgba(252, 157, 154, 1) 70%,
      rgba(247, 67, 124, 1) 100%
    );
    background-size: 200% 200%;
    animation: gradient 10s ease infinite;
  }

  @keyframes gradient {
    0% {
      background-position: 0% 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 50%;
    }
  }
</style>