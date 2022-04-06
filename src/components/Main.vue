<template>
<div class="container-fluid">
    <div class="row text-center">
        <h1 v-if="movies.length != 0" class="text-danger">Films</h1>
        <ul class="d-flex flex-wrap">
            <li v-for="(movie , index) in movies" :key="index + 'movie' + movie.id" class="p-3">
                <div class="imageBox">
                    <div class="imageInn">
                    <img :src="getPoster(movie.poster_path)" alt="" class="img-fluid"> 
                    </div>
                    <div class="hoverImg text-center">
                        <h5 class="text-white">{{movie.overview}}</h5>                  
                        <ul class="d-flex flex-wrap">
                            <li class="stars bg-dark" v-for="(n, index) in getStar(movie.vote_average)" :key="index">&#9733;</li>
                        </ul>                                   
                    </div>
                </div>                                                              
                <h4>{{movie.original_title}}</h4>
                <h5>{{movie.title}}</h5> 
                <div class="text-dark">Lingua:</div> <Lang-flag  :iso ="movie.original_language" />
            </li>         
        </ul>
    </div>  
    <div class="row text-center">
        <h1 v-if="series.length != 0" class="text-danger">Series</h1>
        <ul class="d-flex flex-wrap">
            <li v-for="(serie , index) in series" :key="index + 'movie' + serie.id" class="p-3">
                <div class="imageBox">
                    <div class="imageInn">
                    <img :src="getPoster(serie.poster_path)" alt="" class="img-fluid">
                    </div>                           
                <div class="hoverImg  text-center">
                    <h5 class="text-white">{{serie.overview}}</h5>
                    <ul class="d-flex flex-wrap">
                        <li class="stars bg-dark" v-for="(n, index) in getStar(serie.vote_average)" :key="index">&#9733;</li>
                    </ul>               
                </div>
                </div> 
                <h4>{{serie.original_title}}</h4>
                <h5>{{serie.title}}</h5> 
                <div class="text-dark">Lingua:</div> <Lang-flag  :iso ="serie.original_language" />
                <h6 class="stars"></h6>            
            </li>       
        </ul>
    </div>  
</div>
</template>
<script>
import LangFlag from 'vue-lang-code-flags'
export default {
name: 'MainIndex',
props : ['movies', 'series'],
components : {
    LangFlag,
},
methods: {
    getPoster(path){
        return `https://image.tmdb.org/t/p/w342/${path}`
        },
    getStar(stars){
        return Math.ceil(stars / 2);
    }
},
}
</script>

<style lang="scss">
li{
    border: 2px solid black;
    width: calc(100% / 5);
    list-style-type: none;
    background-color: rgb(238, 230, 224);
}
.stars{
    color: goldenrod;
}
.imageBox {
position: relative;
float: left;
}

.imageBox .hoverImg {
position: absolute;
left: 0;
top: 0;
display: none;
background-color: black;
width: 100%;
height: 100%;
overflow-y: auto;
}

.imageBox:hover .hoverImg {
display: block;
}
</style>
