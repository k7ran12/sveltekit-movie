<script context="module">
    export async function load({fetch}){
        const res = await fetch(
            `https://api.themoviedb.org/3/movie/popular?api_key=8b602b9bd07ee12f35f3ffa0beb7df98&language=en-US&page=1`
            );
            const data = await res.json();            
            if(res.ok){
                return{
                    props: {popular: data.results}
                };
            }
    }
</script>
<script>    
    import PopularMovie from "../components/PopularMovie.svelte";
    import SearchMovies from "../components/SearchMovies.svelte";
    export let popular; 
    import {fly} from 'svelte/transition'   
</script>

<section in:fly={{y: 50, duration: 500, delay: 500}} out:fly={{ duration: 500}}>
    <SearchMovies/>
    <PopularMovie {popular}/>
</section>