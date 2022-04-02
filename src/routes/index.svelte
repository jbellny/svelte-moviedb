<script context="module">
    const APIKey = '1db96023df56673325d7456990fb71c9'

    export async function load() {
        const res = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=${APIKey}&language=en-US&page=1`)
        const data = await res.json()
        if(res.ok) {
            return {
                props: {popular: data.results}
            }
        }
    }

</script>

<script>
    import PopularMovies from "../components/PopularMovies.svelte";
    import SearchMovies from '../components/SearchMovies.svelte'
    export let popular
    import { fly } from 'svelte/transition'
</script>

<section in:fly={{y: 50, duration: 750, delay: 500}} out:fly={{duration: 500}}>
    <SearchMovies />
    <PopularMovies {popular}/>
</section>