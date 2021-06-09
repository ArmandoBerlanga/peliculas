<template>
    <div>
        <h3>Contenido encontrado de: <span>{{contentName}}</span></h3>
        <div class="movies-list">
            <div class="movie" v-for="movie in movies" :key="movie.imdbID">
            <router-link :to="'/movie/' + movie.imdbID" class="movie-link">
            
                <div class="movie-info">
                <div class="movie-poster">
                    <img class="content-img" :src="movie.Poster" alt="No se encontro el poster de la pelicula" />
                    <div class="type"><h5>{{movie.Type}}</h5></div>
                </div>
                
                <div class="movie-detail">
                    <div class="year">{{ movie.Year }}</div>
                    <div class="title">{{ movie.Title }}</div>
                </div>
                </div>

            </router-link>
            </div>
        </div>
    </div>
</template>

<script>

    export default ({
        name: 'MovieList',
        props: ['movies', 'contentName'],
    })

</script>

<style scoped>

    .movies-list {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }

    .movie-poster{
        max-width: 50%;
        flex: 1 1 50%;
        padding-right: 7px;
        padding-left: 7px;
        position: relative;
        display: flex;
        flex-direction: column;
     
    }

    .content-img {
        width: 180%;
        height: 400px;
        object-fit: cover;
        object-position: 0% 0%;
        border-radius: 5px 5px 5px 5px;
    }

    .type{
        position: absolute;
        padding: 7px 14px;
        background-color:#55868C;
        color: white;
        bottom: 56px;
        left: 0px;
        text-transform: capitalize;
        border-radius: 0px 5px 5px 0px;
        border: 0.5px solid white;
        font-weight: bold;
        text-transform: capitalize;
    }

    .movie-detail {
        max-width: 80%;
        margin-bottom: 15px;
        text-align: center;
        margin-top: 10px;
        padding-left: 20px;
    }

    .movie-info {
        transition: transform 250ms;
    }

    .movie-info:hover {
        transform: scale(1.05, 1.05);
    }

    .year{
        color: #55868C;
        font-weight: bold;
    }

    .title {
        font-weight: bold;
    }

    .type h5 {
        margin: 0;
    }

    span {
        color: #55868C;
        font-weight: normal;
    }

</style>
