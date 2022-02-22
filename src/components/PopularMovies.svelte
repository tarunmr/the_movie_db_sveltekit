<script>
    import MovieCard from "./MovieCard.svelte";

    export let popular;
</script>


<div>
    <div style="text-align: center">
        <h3>Popular Movies List</h3>
    </div>
    <div class="popular-movies">
        {#each popular as movie}
            <div>
                <MovieCard {movie}/>
            </div>
        {/each}
    </div>
</div>


<style>
    .popular-movies{
        display: grid;
        grid-template-columns: repeat(auto-fit,minmax(200px,1fr));
        grid-column-gap: 1rem;
        grid-row-gap: 2rem;
    }
</style>