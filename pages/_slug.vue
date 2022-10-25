<template>
    <article>
        <header class="w-full flex justify-between items-center relative">
            <img class="hero_section_circle_blur left-80 absolute w-1/2 blur-2xl opacity-20" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/Blog/hero_circle_blur_brvhQy0LI.svg?ik-sdk-version=javascript-1.4.3&updatedAt=1666111900071" alt="circle blur">
            <img class="logo" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/android-chrome-512x512_exmBxaGLK.png?ik-sdk-version=javascript-1.4.3&updatedAt=1665675785139" alt="logo">
            <!-- <nav>
            <a href="#">About me</a>
            <a href="#">Contact</a>
            </nav> -->
            <a class="pt-3 pb-3 pr-5 pl-5 bg-transparent border-4 border-cta-color rounded-full" href="https://yudaicreator.com">Portfolio</a>
        </header>

        <nuxt-link class="flex items-center mt-4 mb-8 hover:shadow-cta-color" to="/">
            <svg class="mr-1" xmlns="http://www.w3.org/2000/svg" width="14.998" height="15" viewBox="0 0 14.998 20">
                <path id="bxs-left-arrow" d="M4.431,12.822l13,9A1,1,0,0,0,19,21V3a1,1,0,0,0-1.569-.823l-13,9a1,1,0,0,0,0,1.645Z" transform="translate(-4.002 -1.999)" fill="#dae6ff"/>
            </svg>
            Back
        </nuxt-link>

        <nuxt-content class="flex flex-col items-center" :document="article" />
    </article>   
</template>

<script>
export default {
    async asyncData({ $content, params }) {
        const article = await $content('articles', params.slug).fetch();

        return { article }
    }
}
</script>

<style>

.nuxt-content-container{
    display: grid;
    place-content: center;
}

/* .nuxt-content{
    display: grid;
    place-content: center;padding-top: 1rem;
    padding-left: 2rem;
    padding-right: 2rem;
    padding-bottom: 1rem;
} */

.nuxt-content{
    padding-left: 4rem;
    padding-right: 4rem;
}

.nuxt-content h1{
    font-size: 4.5rem;
    margin-top: 2rem;
    align-self: baseline;
}

.nuxt-content h2{
    
    align-self: baseline;
}

.nuxt-content p{
    font-size: 1.5rem;
    font-weight: 200;
    margin-bottom: 2rem;
    align-self: baseline;
}

.nuxt-content img{
    width: 80%;
    max-width: 27rem;
    border: 3px solid #00A1FF;
    border-radius: 10px;

    display: grid;
    place-content: center;
}

@media (max-width: 550px){
    .nuxt-content{
        padding-left: 1rem;
        padding-right: 1rem;
    }
    .nuxt-content h1{
        font-size: 2rem;
    }
    .nuxt-content p{
        font-size: 1rem;
    }
    /* .nuxt-content img{
        font-size: 1rem;
    } */
}


</style>