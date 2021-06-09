<template>
    <div id="movie-detail">
        <h1>Detalle del contenido: <span>{{movie.Title}}</span></h1>
        <div class="movie-display">

            <img :src="movie.Poster" alt="No se encontro el poster de la pelicula">
            <div class="movie-info">
                <div class="part"><span class="info">Trama: </span>{{movie.Plot}}</div>
                <div class="part"><span class="info">Tipo: </span>{{movie.Type}}</div>
                <div class="part"><span class="info">Director: </span>{{movie.Director}}</div>
                <div class="part"><span class="info">Productora: </span>{{movie.Production}}</div>
                <div class="part"><span class="info">Lanzamiento: </span> {{movie.Released}}</div>
                <div class="botones">
                    <a href="https://www.netflix.com/browse"><button class="ver">VER</button></a>
                    <a href="/"><button class="return">DEVOLVER</button></a>
                </div>
            </div>

        </div>
    </div>
</template>

<script>

    import { ref, onBeforeMount } from 'vue'
    import { useRoute } from 'vue-router'
    import env from '@/env.js' 

    export default {
        name: 'MovieDetail',
        setup(){
            
            const movie = ref({});
            const route = useRoute()

            onBeforeMount(()=> {
                fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
                    .then(response => response.json())
                    .then (data => {
                        movie.value = data;
                        console.log(data);
                    });
            });

            return {
                movie,
            }
        }
    }

</script>

<style scoped>
    #movie-detail{
        margin: 10px 5%;
    }

    span {
        color: #55868C;
        font-weight: normal;;
    }

    .info {
        font-weight: bold;
    }

    img {
        border-radius: 5px;
    }

    .movie-display {
        display: flex;
        flex-direction: row;
        background-color: aliceblue;
        border-radius: 5px; 
        border: 1px solid rgba(0, 0, 0, 0.089); 
        padding: 1px;  
        transition: transform 250ms;
    }

    .movie-display:hover{
        transform: scale(1.05, 1.05);
    }

    .movie-info {
        padding-top: 15px;
        margin: 5px 2%;
    }

    .part {
        margin-bottom: 10px;
    }

    .botones{
        float: right;
        margin: 5px 2%;
    }

    button {
        padding: 5px 15px;
        border: 0;
        border-radius: 5px;
        margin-left: 5px;
        font-size: 0.9em;
        transition: transform 250ms;
    }

    button:hover {
        transform: translateY(-4px);
        box-shadow: 0px 1px rgba(0, 0, 0, 0.466);
    }


    .ver{
        background-color: #55868C ;
        color: white;
    }

    

</style>