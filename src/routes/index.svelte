<script context="module">
    export async function load({fetch}){
        const res =await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=d17d7936fd661efc6409d85a6d9bf51e`);
        const data = await  res.json();
        if(res.ok){
            return {
                props:{popular:data.results}
            }
        }
    }
</script>

<script>
    import PopularMovies from "../components/PopularMovies.svelte";
    import SearchMovies from "../components/SearchMovies.svelte";
    import {fly} from "svelte/transition";
    export let popular;
</script>


<div in:fly={{y:50,duration:500,delay:500}} out:fly={{duration:500}}>
    <SearchMovies/>
    <PopularMovies {popular}/>

</div>