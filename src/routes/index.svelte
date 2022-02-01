<script context="module">
    export async function load({ fetch }) {
        const res = await fetch (
            `https://api.themoviedb.org/3/movie/popular?api_key=ad3ac39be2d897e739073e87d9559d93&language=ru-RU&page=1`
        );
        const data = await res.json();
        console.log(data);
        if (res.ok) {
            return {
                props: { popular: data.results }
            }
        }
    }
</script>

<script>
    import global from '../global.css'
    import PopularMovies from '../components/PopularMovies.svelte';
    export let popular;
</script>

<section>
    <PopularMovies {popular} />
</section>
