<script>
    import { blogs } from './blogs'
    /**
   * @type {never[]}
   */
    let categories = []

    /**
   * @type {never[]}
   */
    export let filters = []
    export let filterAll = true

    blogs.forEach(blog => {
        if (blog.Published == true) {
            blog.Categories.forEach(category => {
                if (!categories.includes(category)) {
                    categories.push(category)
                }
            })
        }
    })

    
</script>

<div id="filters" data-categories="{ categories }">
    <ul class="">
        <li class="d-flex justify-content-end col-12">
            <label for="all" class="px-3">all</label><input type="checkbox" id="all" name="all" value="all" onclick="toggleFilterAll(event)" bind:checked={filterAll}>
        </li>
        
        {#each categories as category}
            <li class="d-flex justify-content-end col-12 filter-label">
                <label for="{category}" class="px-3">{category}</label><input class="filterCheckBox" type="checkbox" bind:group={filters} id="{category}" name="{category}" value="{category}" onclick="updateFilters('{category}')">
            </li>
        {/each}
    </ul>
</div>

<style>
    li {
        list-style-type: none;
    }

    input {
        /* -webkit-appearance: none;
        -moz-appearance: none;
        appearance: none; */
        /* width: 0.8rem;
        height: 0.8rem; */
        border: black solid 1px;
        background-color: white;
        color: black;
        border-radius: 0;
        outline: none;
        
    }

    input:checked {
        background-color: black;
        outline: none;
    }
</style>

