<template>
    <div class="cb-containter">
        <form class="search-box" @submit.prevent="searchMovies">

            <label class="sb-item" for="box">Barra de busqueda</label>
            <input class="sb-item" name="box" type="text" placeholder="What are looking for?" v-model="search"/>
            <button class="sb-item button">SEARCH</button>

        </form>
    </div>
</template>

<script>
    import { ref } from 'vue'
    import env from '@/env.js'

    export default ({
        name: 'SearchBox',
        setup(props, context){
            const search = ref("");
            const movies = ref([]);

            const searchMovies = () => {
                if (search.value != "") {
                    fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
                        .then(response => response.json())
                        .then (data => {
                            movies.value = data.Search
                            console.log(movies.value)
                            context.emit("search", movies.value, search.value);
                            search.value = ""
                        });
                }
            };

            return {
                search,
                movies,
                searchMovies
            }
        }
    })

</script>

<style scoped>

    .search-box {
        display: flex;
        flex-direction: column;
        align-items: center;
        background-color:#202030 ;
        border-radius: 5px;
        padding: 10px;
    }

    .sb-item {
        margin: 5px;
    }

    label {
        font-size: 1.5em;
        font-weight: bold;
        color: white;
    }

    input {
        width: 100%;
        height: 2.5em;
        border-radius: 5px;
        text-align: center;
    }

    ::placeholder {
        text-align: center;
        color: rgb(184, 194, 194);
    }

    .button {
        background-color: #55868C;
        width: 25%;
        border-radius: 5px;
        border: 0;
        color: white;
        padding: 5px;
        transition: transform 250ms;
        font-weight: bold;
    }

    .button:hover {
        transform: scale(1.1, 1.1);
    }

    .button:active {
        background-color: #FFAD05;
    }

</style>
