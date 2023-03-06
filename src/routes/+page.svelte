<script>
    // import About from "./About.svelte";
    // import { onMount } from "svelte";
    import { blogs } from './blogs'
    import BlogPreview from './BlogPreview.svelte'
    // import BlogFilter from './BlogFilter.svelte'


    /**
   * @type {any[]}
   */
    let categories = []
    /**
   * @type {any[]}
   */
    let filters = []
    let filterAll = true

    

    function toggleFilter(category) {
        if (filters.includes(category)) {
            filters.splice(filters.indexOf(category), 1)
        } else {
            filters.push(category)
        }
        if (filters.length < 1) {
            filterAll = true
        } else {
            filterAll = false
        }
    }

    function toggleFilterAll() {
        console.log('all')
        filterAll = true
        filters = []
    }

    blogs.forEach(blog => {
        if (blog.Published == true) {
            blog.Categories.forEach(category => {
                if (!categories.includes(category)) {
                    categories.push(category)
                }
            })
        }
    })

    $: if (filters.length < 1) {
        filterAll = true;
    }

</script>

<div id="about" class="px-5">
    <nav class="col-12 d-flex justify-content-end align-content-center align-items-center header">
        <a id="back-to-home" onclick='goToHome()'>
            <h2 class="d-inline d-md-none">h</h2>
            <h2 class="d-none d-md-inline">home</h2>
        </a>
    </nav>
    
    <section class="col-12 d-flex justify-content-center flex-wrap content-container">
        <h1>About</h1>
        <p>Must go faster... go, go, go, go, go! Hey, you know how I'm, like, always trying to save the planet? Here's my chance. This thing comes fully loaded. AM/FM radio, reclining bucket seats, and... power windows. Must go faster. I gave it a cold? I gave it a virus. A computer virus.
            <br><br>
            Yeah, but John, if The Pirates of the Caribbean breaks down, the pirates don’t eat the tourists. I was part of something special. We gotta burn the rain forest, dump toxic waste, pollute the air, and rip up the OZONE! 'Cause maybe if we screw up this planet enough, they won't want it anymore!</p>
    </section>
</div>



<div id="home" class="active d-flex justify-content-center flex-wrap px-5">
    <nav class="col-12 d-flex justify-content-between align-content-center align-items-center header ">
        <a id="to-about" onclick='goToAbout()'>
            <h2 class="d-inline d-md-none">a</h2>
            <h2 class="d-none d-md-inline">about</h2>
        </a>
        
        <h1>morganfolz.blog</h1>
        <a id="blog-filter-toggle" onclick='toggleFilterMenu()'>
            <h2 class="d-inline d-md-none">b</h2>
            <h2 class="d-none d-md-inline">topics</h2>
        </a>
    </nav>
    
    
    
    <div class="col-12 col-md-8 col-lg-6 d-flex justify-content-center flex-wrap content-container mt-4">
        {#each blogs as blog}
            {#if filterAll == true} 
                {#if blog.Published == true}  
                    <BlogPreview { blog } />
                {/if}
            {:else}
                {#if blog.Published}
                    {#each blog.Categories as category}
                        {#if filters.includes(category)}
                            <BlogPreview { blog } />
                        {/if}
                    {/each}
                {/if}
            {/if}
        {/each}
    </div>

    <div id="blog-filter-container" class="">
        <div id="filters" data-categories="{ categories }">
            <ul class="">
                <li class="d-flex justify-content-end col-12">
                    <label for="all" class="px-3">all</label><input type="checkbox" id="all" name="all" value="all" on:click={toggleFilterAll} bind:checked={filterAll}>
                </li>
                
                {#each categories as category}
                    <li class="d-flex justify-content-end col-12 filter-label">
                        <label for="{category}" class="px-3">{category}</label><input class="filterCheckBox" type="checkbox" bind:group={filters} id="{category}" name="{category}" value="{category}" on:click={toggleFilter}>
                        <!-- <label for="{category}" class="px-3">{category}</label><input class="filterCheckBox" type="checkbox" bind:group={filters} id="{category}" name="{category}" value="{category}" onclick="updateFilters('{category}')"> -->
                    </li>
                {/each}
            </ul>
        </div>
    </div>

</div>

<!-- <div id="about-mobile">
    <About />
</div> -->





<style>

    a:hover {
        cursor: pointer;
    }

</style>