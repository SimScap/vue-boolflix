<template>
<main>
<div class="container-fluid">
    <div class="row text-center">
        <div class="col-12" v-if="movies.length != 0">
            <h1  class="text-danger">Films</h1>
            <ul class="d-flex flex-wrap ">
            <li v-for="(movie , index) in movies" :key="index + 'movie' + movie.id" class="p-3">
                <div class="imageBox">
                    <div class="imageInn">
                    <img :src="getPoster(movie.poster_path)" alt="" class="img-fluid"> 
                    </div>
                    <div class="hoverImg">
                <h5><span class="text-danger">Titolo:</span> {{movie.original_title}}</h5>
                <h5 class="text-warning">Language: <span><Lang-flag  :iso ="movie.original_language" /></span></h5> 
                        <h5 class="text-white text-center"><span class="text-secondary">Overview: </span>{{movie.overview}}</h5>                                         
                        <span class="stars bg-dark" v-for="(n, index) in getStar(movie.vote_average)" :key="index">&#9733;</span>                                                     
                    </div>
                </div>                                                              
            </li>         
        </ul>
        </div>    
        <div v-else class="text-white p-5">
            <h1>Cosa aspetti, scegli un titolo...</h1>
            </div>    
    </div>  
    <div class="row text-center">
        <div class="col-12">
        <h1 v-if="series.length != 0" class="text-danger">Series</h1>
        <ul class="d-flex flex-wrap">
            <li v-for="(serie , index) in series" :key="index + 'movie' + serie.id" class="p-3">
                <div class="imageBox">
                    <div class="imageInn">
                    <img :src="getPoster(serie.poster_path)" alt="" class="img-fluid">
                    </div>                           
                    <div class="hoverImg  text-center">
                    <h5 class="text-white">{{serie.overview}}</h5>                 
                    <div class="stars" v-for="(n, index) in getStar(serie.vote_average)" :key="index">&#9733;</div>           
                </div>
                </div> 
                <h4>{{serie.original_title}}</h4>
                <h5>{{serie.title}}</h5> 
                <div class="text-dark">Lingua:<Lang-flag  :iso ="serie.original_language" /></div> 
                <h6 class="stars"></h6>            
            </li>       
        </ul>
        </div>     
    </div>  
</div>
</main>

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
limitOverview() {
    if (this.movies.overview.length > 100) {
        return this.movies.overview.slice(0, 50) + "...";
    } else {
        return this.movies.overview;
    }
    },
}
</script>

<style lang="scss">
li{
    border: 2px solid rgb(113, 113, 113);  
    list-style-type: none;
    background-color: rgb(29, 29, 29);
    //width: calc(100% / 5);
    width: 250px;
    color: white;
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
main{
    height: calc(100vh - 100px);
    overflow-y: auto;
}
</style>
