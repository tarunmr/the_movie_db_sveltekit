<script context="module">
    export async function load({fetch,params}){
        const res =await fetch(`https://api.themoviedb.org/3/movie/${params.id}?api_key=d17d7936fd661efc6409d85a6d9bf51e&language=en-US`);
        const movieDetail = await  res.json();
        if(res.ok){
            return {
                props:{movieDetail}
            }
        }
    }
</script>

<script>
    import {fly} from "svelte/transition";
    export let movieDetail;
</script>


<div class="movie-detail" in:fly={{y:50,duration:500,delay:500}} out:fly={{duration:500}}>
    <div class="img-container">
        <img src={'https://image.tmdb.org/t/p/original'+movieDetail.poster_path} alt={movieDetail.title}>
    </div>
    <div class="text-container">
        <h1>{movieDetail.title}</h1>
        <p class="overview">{movieDetail.overview}</p>
        <p>
            <span>Release Date:</span>
            {movieDetail.release_date}<br/>
            <span>Budget</span>
            ${movieDetail.budget}<br/>
            <span>Rating:</span>
            {movieDetail.vote_average}<br/>
            <span>Runtime:</span>
            {movieDetail.runtime}mins
        </p>
    </div>
</div>


<style>
    .movie-detail{
        margin: 2rem 10%;
    }
    span{
        font-weight: bold;
    }
    h1{
        padding: 1rem 0 2rem;
    }
    p{
        padding: 1rem 0;
    }
    .img-container{
        width: 100%;
    }
    img{
        width: 100%;
        border-radius: 1rem;
        height: 60vh;
        object-fit: cover;
    }
</style>