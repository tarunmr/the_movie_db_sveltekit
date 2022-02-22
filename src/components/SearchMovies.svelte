<script>
    import {goto} from "$app/navigation";
    import {fly} from "svelte/transition";

    let searchInputValue='';
    let active=false;
    function cancelInActive(){
        active = !!searchInputValue;
    }

    function formSubmit(){
        goto('/search/'+searchInputValue)
    }
</script>

<form on:submit|preventDefault={formSubmit}  class="search">

    {#if !active}
        <label in:fly={{y:-10,duration:500}} out:fly={{y:-10,duration:500}} for="search_movies">Search</label>
    {/if}

    <input on:blur={cancelInActive}
           on:focus={()=>active=true}
           bind:value={searchInputValue}
           name="search_movies"
           type="text"
           class={active?'selected':''}
    />

    {#if active}
          <button in:fly={{x:20,duration:500}} out:fly={{x:0,duration:500}}>Search</button>
    {/if}
</form>


<style>
    .search{
        position: relative;
        width: 30%;
        margin: 1rem;
    }
    button{
        font-size: 0.7rem;
        padding: 0 1rem;
        background: rgb(96,110,201);
        color: white;
        font-weight: bold;
        border: none;
        position: absolute;
        bottom: 50%;
        right: 0;
        transform: translate(0,50%);
        height: 100%;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
        cursor: pointer;
    }
    input {
        width: 100%;
        border: none;
        font-size: 1rem;
        outline: none;
        color: rgb(255,255,255);
        transition: background 0.75s ease-out;
        font-weight: bold;
        background: rgb(63,63,63);
        border-radius: 10px;
        padding: 1rem;
    }
    label{
        position: absolute;
        font-size: 0.8rem;
        top: 50%;
        left: 0;
        transform: translate(0,-50%);
        pointer-events: none;
        color: #fff;
        padding: 0 1rem;
    }
    input.selected{
        background: rgb(50,50,50)!important;
    }
</style>