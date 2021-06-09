<template>
    <div class="feature-card">

        <img src="https://s3-us-west-2.amazonaws.com/flx-editorial-wordpress/wp-content/uploads/2018/03/13153742/RT_300EssentialMovies_700X250.jpg" 
          alt="Naruto Poster" class="featured-img">

        <div class="detail">
          <h3>Buscador de peliculas y series</h3>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Aut, expedita laborum? Rerum, natus a! Autem pariatur minus deleniti deserunt laboriosam, 
            harum totam eum quidem accusantium? Deleniti id minima commodi enim?
          </p>
        </div>

    </div>
</template>

<script>

    export default ({
        name: 'FeatureCard',
        setup() {
        }
    })

</script>

<style scoped>

    .feature-card {
        position: relative;
        transition: transform 250ms;
    }

    .feature-card:hover {
        transform: scale(1.03, 1.03);
    }

    .feature-card .featured-img {
        display: block;
        width: 100%;
        height: 300px;
        object-fit: cover;
        object-position: 50% 0%;
        position: relative;
        z-index: 0;
        border-radius: 5px;
        margin-bottom: 10px;
    }

    .detail {
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        padding: 0px 20px 10px 30px;
        color: white;
        background-color: rgba(0, 0, 0, 0.548);
        border-radius: 0px 0px 5px 5px;
    }

    .detail h3 {
        font-weight: bold;
    }

</style>