<script>
    export let movie;
    console.log(movie);
</script>

<div class="movie_card">
    <img 
        src={'https://image.tmdb.org/t/p/w500' + movie.poster_path} 
        alt={movie.original_title}
    />
    <div class="movie_description">
        <h2>{movie.original_title} / {movie.title}</h2>
        <p>{movie.release_date}</p>
    </div>

</div>

<style lang="scss">
    .movie_card {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        padding: 1rem;
    }

    img {
        width: 100%;
        object-fit: cover;
        border-radius: 1rem;
        margin: 0 0 1rem 0;
    }

    .movie_description {
        height: 5vh;
    }

    h2 {
        font-size: 0.9rem;
    }

    p {
        font-size: 0.7rem;
    }


</style>
