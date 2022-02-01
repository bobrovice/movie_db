<script context="module">
    export async function load({ fetch, params }) {
        const res = await fetch (
            `https://api.themoviedb.org/3/movie/${params.id}?api_key=ad3ac39be2d897e739073e87d9559d93&language=ru-RU&page=1`
        );
        const movieDetail = await res.json();

        if (res.ok) {
            return {
                props: { movieDetail }
            }
        }
    }
</script>

<script>
    export let movieDetail;
</script>

<div class="movie_detail">
    <div class="img_container">
        <img 
            src={'https://image.tmdb.org/t/p/original' + movieDetail.backdrop_path} 
            alt={movieDetail.original_title}
        />
    </div>
    <div class="txt_container">
        <h1>{movieDetail.original_title} / {movieDetail.title}</h1>
        <p class="overview">{movieDetail.overview}</p>
        <p>
            <span>Release Date:</span>
            {movieDetail.release_date}<br />
            <span>Budget:</span>
            $ {movieDetail.budget}<br />
            <span>Rating:</span>
            {movieDetail.vote_average}<br />
            <span>Runtime:</span>
            {movieDetail.runtime}mins
        </p>
    </div>
</div>

<style>
    h1 {
        padding: 1rem 0rem 2rem;
    }
    p {
        padding: 1rem 0rem;
    }
    .img_container {
        width: 100%;
    }
    img {
        width: 100%;
        border-radius: 1rem;
    }
    .movie_detail {
        margin: 2rem 20%;
    }
    span {
        font-weight: bold;
    }
</style>
