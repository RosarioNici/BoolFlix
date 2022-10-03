<template>
    <div>
            <div class="container row" > 
                <div class="card mx-2">
                    <div class="img-hover">
                        <img class="img-fluid" :src="imgPath(film.poster_path)" alt="">
                    </div>
                    <div class="text">
                        <ul class="list-unstyled"><h5>{{film.title}}</h5>
                            <li class="px-3"><h6>Titolo Originale: </h6>{{film.original_title}}</li>
                            <li class="px-3"><h5>Lingua: </h5><img :src="addFlag(film.original_language)"></li>
                            <li class="px-3"><h5>Voto: </h5>{{film.vote_average}}</li>
                        </ul> 
                     </div>
                </div>
                
            </div>
    </div>
</template>

<script>




export default {
    name: 'moviesComponent'  ,
    props:{
    film:Object
   },
   methods:{
    imgPath(codeImg){
        return `https://image.tmdb.org/t/p/w500/${codeImg}`
             
    },
    addFlag(flag){
        return `../assets/1x1/${flag}.svg`
    }
        }}
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