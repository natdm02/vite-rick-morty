<script>  
  export default {
    props:{
      name: String,
      status: String,
      species: String,
      image: String,
    }
  }
</script>


<template>
  <div class="card" style="width: 18rem;">
  <img :src="image" class="card-img-top p-3" alt="...">
  <div class="card-body">
    <h5 class="card-title">{{ name }}</h5>
    <hr>
    <p class="card-text">{{ status }}</p>
    <p class="card-text">{{ species }}</p>
  </div>
</div>
</template>


<style lang="scss" scoped>
  .card{
    border-radius: 25px;
    box-shadow: 
    rgba(0, 0, 0, 0.17) 0px -23px 25px 0px inset, 
    rgba(0, 0, 0, 0.15) 0px -36px 30px 0px inset, 
    rgba(0, 0, 0, 0.1) 0px -79px 40px 0px inset, 
    rgba(0, 0, 0, 0.06) 0px 2px 1px, 
    rgba(0, 0, 0, 0.09) 0px 4px 2px, 
    rgba(0, 0, 0, 0.09) 0px 8px 4px, 
    rgba(0, 0, 0, 0.09) 0px 16px 8px, 
    rgba(0, 0, 0, 0.09) 0px 32px 16px;
    transition: transform 0.3s ease;
    
    &:hover{
      transform: scale(1.1);
    }

    .square-img-container {
    width: 100%;
    padding-top: 100%; /* Imposta l'altezza in base alla larghezza per ottenere un quadrato */
    position: relative;
    overflow: hidden;
  }

  img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover; /* Scalare l'immagine per riempire completamente il contenitore */
    border-radius: 25px; /* Assicurati che l'immagine sia arrotondata insieme al contenitore */
  }

  }
</style>