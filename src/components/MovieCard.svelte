<script>
    export let movie;
</script>


<div class="movie-card">
    <div>
        <a sveltekit:noscroll sveltekit:prefetch href={"/movie/"+movie.id}>
            <img src={'https://image.tmdb.org/t/p/w500'+movie.poster_path} alt={movie.title}>
        </a>
        <div class="description">
            <h3>{movie.title}</h3>
            <p>{movie.release_date}</p>
        </div>
    </div>
</div>


<style>
    img {
        width: 100%;
        height: auto;
        border-radius: 1rem;
        margin-bottom: 1rem;
    }
    h3 {
        font-size: 1rem;
    }
    p  {
        font-size: 0.8rem;
    }
    .description{
        height: 5vh;
    }
    .movie-card{
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        padding: 1rem;
    }
</style>


