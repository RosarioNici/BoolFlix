<template>
    <div>
      <div class="container row"> 
          <div class="card m-2">
              <div class="img-hover">
                  <img class="img-fluid" :src="imgPath(serie.poster_path)" alt="">
              </div>    
              <div class="text">
                  <ul class="list-unstyled"><h4>{{serie.name}}</h4>
                      <li class="px-5"><h5>Titolo Originale: </h5>{{serie.original_name}}</li>
                      <li class="px-5">Lingua: {{serie.original_language}}</li>
                      <li class="px-5"><h5>Voto: </h5>{{serie.vote_average}}</li>
                  </ul> 
              </div>
               
          </div> 
         
      </div>
    </div>
  </template>
  
  <script>
  
  export default {
      name: 'seriesComponent',
  props:{
      serie:Object
  }, 
  methods:{
      imgPath(codeImg){
          return `https://image.tmdb.org/t/p/w500/${codeImg}`
               
      }
          }
  
  
  
  
  }
  </script>
  
  <style lang="scss" scoped>
    .img-hover{
      position: relative;
    }
    .text{
      color: white;;
    position: absolute;
    top: 20%;
    visibility: hidden;
    }
  .card:hover{
      background-color: black;
  }
  .card:hover .img-hover{
      opacity: 0;
  }
  .card:hover .text{
     visibility: visible;
  }
  
  </style>
  