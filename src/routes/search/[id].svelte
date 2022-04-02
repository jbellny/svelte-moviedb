<script context="module">
    const APIKey = '1db96023df56673325d7456990fb71c9'

    export async function load({params}) {
        let movieId = params.id
        const res = await fetch(`https://api.themoviedb.org/3/search/movie?api_key=${APIKey}&language=en-US&query=${movieId}&page=1&include_adult=false`)
        const data = await res.json()
        if(res.ok) {
            return {
                props: {searchResults: data.results}
            } 

            } else {
                return {
                    props: {searchResults: data.results}
                }
            }
    }

</script>

<script>
    import MovieCard from '../../components/MovieCard.svelte'
    export let searchResults
</script>

<h3>Search Results</h3>
<div class="search-results">
        {#each searchResults as movie}
            <MovieCard {movie}/>
        {/each}
</div>

<style>
    h3 {
        padding: 0 1rem;
    }
    .search-results {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px,1fr));
        grid-column-gap: 1rem;
        grid-row-gap: 2rem;
    }
</style>