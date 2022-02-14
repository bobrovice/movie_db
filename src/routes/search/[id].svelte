<script context="module">
    export async function load({ fetch, params }) {
        const res = await fetch (
            `https://api.themoviedb.org/3/search/movie?api_key=ad3ac39be2d897e739073e87d9559d93&language=ru-RU&page=1&query=${params.id}&include_adult=false`
        );
        const data = await res.json();
        console.log(data);
        if (res.ok) {
            return {
                props: { searchedMovie: data.results }
            }
        }
    }
</script>

<script>
    import MovieCard from '../../components/MovieCard.svelte'
    export let searchedMovie
</script>

<div class="searched-movies">
    {#each searchedMovie as movie}
        <MovieCard {movie} />
    {/each}
</div>

<style>
    .searched-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-gap: 2rem 2rem;
        height: 20vh;
    }
</style>