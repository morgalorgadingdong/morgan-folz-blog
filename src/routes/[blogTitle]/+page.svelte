<script>
	import { blogs } from "../blogs"; 
    export let data;
    //  export let blog;
    //  export const slug = blog;
    
    let blog
    blogs.forEach(article => {
        if (article.Title == data.blogTitle) {
            blog = article;
        }
    })

    
    // let imgSrcBanner = `../img/blogs/${blog.Number}. ${blog.Title}/blog${blog.id}-banner.jpg`;
    let imgSrcBanner = `../img/blog/${blog.id}. ${blog.Title}/blog${blog.id}-banner.jpg`;
    let currentImg = 1;
    let testBlog = blogs[1]
    let prevBlog
    let nextBlog
    // if (blog.Number != 1) {
    //     prevBlog = blogs[blog.Number - 1]
    // }
    // if (blog.Number <= blogs.length+1) {
    //     nextBlog = blogs[blog.Number + 1]
    // }

</script>

<section>
    <nav class="col-12 d-flex justify-content-start align-content-center align-items-center header">
        <a id="back-to-home" href="/">
            <h2 class="d-inline d-md-none">h</h2>
            <h2 class="d-none d-md-inline">home</h2>
        </a>
    </nav>
    <div class="blogBanner col-12 px-0">
        <img src = {imgSrcBanner} alt="{blog.BannerAlt}" class="bannerImg" />
    </div>
    <div id="" class="d-flex flex-wrap justify-content-center content-container text-start center mb-5" >            
        <div class="col-12 blog-header d-flex align-content-center justify-content-start flex-wrap">
            <h2 class="col-12 text-left px-3 pb-1">{blog.Title}</h2>
            <p class="blogDate col-12 text-left px-3">Published by {blog.Author} on {blog.Date}</p>
        </div>
        <div class="col-12 px-3">
            <div class="blog-divider col-12 blog-header-divider"></div>
        </div>
        <div class="col-12 d-flex justify-content-center flex-wrap mt-3 px-3">
            {#each blog.Sections as Section}
                {#if Section.Type == 'text'}
                    <p class="col-12 text-left px-0 my-3 blog-text">{Section.Content}</p>
                {:else if Section.Type == 'img'}
                    <img src="./img/blogs/{blog.Number}. {blog.Title}/blog{blog.id}-{currentImg}.jpg" alt="{Section.Alt}" class="col-10 col-md-8 mt-5 blog-img" />
                    <span class="col-12 text-center mb-5">{Section.Caption} <a href="{Section.Src}">source</a></span>
                    { currentImg = currentImg + 1}  
                {:else if Section.Type == 'divider'}
                    <div class="mt-5 pb-5 blog-divider col-8"></div>
                {:else if Section.Type == 'highlight'}
                <p class="text-center blog-highlight p-5 col-12 col-lg-8 my-5">{Section.Content}</p>
                {:else if Section.Type == 'heading'}
                <h4 class="text-start col-12 mt-3 mb-0">{Section.Content}</h4>
                {/if}
            {/each}
        </div>
    </div>
    <a href="/" class=""><div class="button my-5">Back to Blogs</div></a>
    <!-- <a href={'./'+testBlog.Title}>{testBlog.Title}</a>  -->
    <!-- <p on:click={blog = testBlog}>{testBlog.Title}</p> -->
</section>
 <!-- <p on:click={reloadPage(nextBlog.Title)}>{nextBlog.Title}</p> -->

<style>
    .blog-text {
        font-size: 1.2rem;
        line-height: 1.5rem;
        font-family: var(--bs-body-font-family);
    }

    .blog-img {
        object-fit: cover;
        margin: 0;
        position: relative;
        left: 0;
        top: 0;
        aspect-ratio: 1/1;
    }

    .blogBanner {
        background-color: black;
        height: 30vh;
        max-height: 300px;
        /* background-position: center;
        background-repeat: no-repeat;
        background-size: cover; */
        position: relative;
        margin: auto;
        /* background-position: center; */
    }

    .blogBanner > img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        margin: 0;
        position: absolute;
        left: 0;
        top: 0;
        /* mask-image: linear-gradient(rgba(0, 0, 0, 0.2), rgba(0, 0, 0, 0.2));
        -webkit-mask-image: linear-gradient(rgba(0, 0, 0), rgba(0, 0, 0)); */
    }
/* #blogsContainer {
    display: flex;
    gap: 15px;
} */

.blog-header {
    height: 23vh;
}

.blogDate {
    color: #afadac;
}

.blog-header-divider {
    margin-bottom: 40px;
}

a {
    color: black;
}

.blog-highlight {
    font-size: 1.5rem;
    font-weight: 600;
    color: black;
    font-style: italic;
    background-color: rgb(175, 173, 172, 0.1);
}

.blog-divider {
    border-top: black solid 2px;
}
</style>