<script>
    /**
	 * @type {{ }}
	 */
    export let blog;
    let imgSrc = `./img/blog/${blog.id}. ${blog.Title}/blog${blog.id}-banner.jpg`;
    // let imgSrc = `./img/test.jpg`;
    // console.log(imgSrc)
</script>
<div class="blog-preview col-12 mb-5">
    <div class="img-container">
        <a href="/{blog.Title}"><img src="{ imgSrc }" class="img" alt=""></a>
    </div>
    <div class="blog-info col-12 d-flex justify-content-between align-items-center">
        <h3 class="blog-title my-2"><a href="/{blog.Title}">{blog.Title}</a></h3>
        <p class="blog-date m-0">{blog.Date}</p>
    </div>
    <div id="blog-category-container" class="category-container col-12 d-flex justify-content-center">
        {#each blog.Categories as category}
            <span class="category">{category}</span>
        {/each}
    </div>
</div>


<style>
    a {
        text-decoration: none;
        color: black;
    }
    #blog-category-container {
        opacity: 0;
        transform: translateY(-100%);
        transition: all 0.5s ease-in-out;
    }

    #blog-category-container .category {
    /* display: inline-block; */
    padding: 0.5rem 1rem 0.5rem 1rem;
    margin: 0 0.5rem 0 0.5rem;
    /* border: solid 1px black; */
    transition: all 0.5s ease-in-out;
    box-shadow: -2px 2px 4px 0px rgba(0,0,0,0.5);
    }

    .blog-preview:hover > #blog-category-container {
        opacity: 1;
        transform: translateY(0%);
        transition: all 0.5s ease-in-out;
    }

</style>