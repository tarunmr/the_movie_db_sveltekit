<script context="module">
    export async function load({fetch,params}){
        const res =await fetch(`https://api.themoviedb.org/3/search/movie?api_key=d17d7936fd661efc6409d85a6d9bf51e&language=en-US&query=${params.id}&page=1&include_adult=false`);
        const data = await  res.json();
        if(res.ok){
            return {
                props:{searchedMovies:data.results}
            }
        }
    }
</script>


<script>
    import MovieCard from "../../components/MovieCard.svelte";

    export let searchedMovies;
</script>

<div class="searched-movies">
    {#each searchedMovies as movie}
        <MovieCard {movie}/>
    {/each}
</div>


<style>
    .searched-movies{
        display: grid;
        grid-template-columns: repeat(auto-fit,minmax(200px,1fr));
        grid-column-gap: 1rem;
        grid-row-gap: 2rem;
    }
</style>