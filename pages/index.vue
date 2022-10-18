<template>
  <div class="main_container relative">
    <div class="hero_wrapper h-screen relative">
      <header class="w-full flex justify-between items-center relative">
        <img class="hero_section_circle_blur left-96 absolute w-1/2 blur-2xl opacity-20" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/Blog/hero_circle_blur_brvhQy0LI.svg?ik-sdk-version=javascript-1.4.3&updatedAt=1666111900071" alt="circle blur">
        <img class="logo" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/android-chrome-512x512_exmBxaGLK.png?ik-sdk-version=javascript-1.4.3&updatedAt=1665675785139" alt="logo">
        <!-- <nav>
          <a href="#">About me</a>
          <a href="#">Contact</a>
        </nav> -->
        <a class="pt-3 pb-3 pr-5 pl-5 bg-transparent border-4 border-cta-color rounded-full" href="https://yudaicreator.com">Portfolio</a>
      </header>
      <section class="hero_section w-full mt-28 mb-8 relative">
        <!-- <div class="hero_section_circle_blur bg-cta-color w-1/2 h-72 rounded-full"></div> -->
        <h1 class="text-9xl">My Personal Log</h1>
        <p class="text-2xl mt-4">Hi, Yudai here. Welcome to this space within my system. 
          I write about Frontend Development, UI Design, and share
          some of thoughts from my experience. Happy reading.
        </p>
        <div class="hero_social_links mt-4 flex items-center">
          <a href="https://twitter.com/creator_yudai" target="_blank">
            <img class="w-7" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/Blog/bxl-twitter_1__hV_d7GVpE.svg?ik-sdk-version=javascript-1.4.3&updatedAt=1666112463572" alt="twitter link">
          </a>
          <a class="ml-8" href="https://www.linkedin.com/in/yudai-h-911bb01bb/" target="_blank">
            <img class="w-7" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/Blog/bxl-linkedin-square_1__XfGKRz2rx.svg?ik-sdk-version=javascript-1.4.3&updatedAt=1666112463575" alt="linkedin link">
          </a>
          <a class="ml-8" href="https://www.instagram.com/creator_yudai/" target="_blank">
            <img class="w-7" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/Blog/bxl-instagram_LKcQRGsy5.svg?ik-sdk-version=javascript-1.4.3&updatedAt=1666112463595" alt="instagram link">
          </a>
          <a class="ml-8" href="https://www.instagram.com/creator_yudai/" target="_blank">
            <img class="w-7" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/Blog/bxl-youtube_RfHZRg1AB.svg?ik-sdk-version=javascript-1.4.3&updatedAt=1666113204665" alt="youtube link">
          </a>
        </div>
        <img class="bg_img absolute opacity-10 w-1/2 left-1/2" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/Blog/Reading_glasses-cuate_qHjpoUd1H.svg?ik-sdk-version=javascript-1.4.3&updatedAt=1665677235075" alt="reading and writing">
      </section>
    </div>
    

    <section class="posts">
      <div class="post mb-8" v-for="post of posts" :key="post">
        <nuxt-link class="flex" :to="{name: 'slug', params: {slug: post.slug}}">
          <img class="post_featured_image" :src="`${post.img}`" alt="featured image">
          <div class="post_details_wrapper ml-8">
            <div class="post_details">
              <h3 class="text-4xl font-bold">{{post.title}}</h3>
              <div class="post_details_data">
                <span class="mr-2">{{post.date}}</span>
                *
                <span class="ml-2 mr-2">{{post.read}}</span>
                *
                <span class="text-cta-color ml-2 mr-2">{{post.tag}}</span>
              </div>
              <p class="max-w-5xl mt-6">{{post.description}}</p>

              <span class="text-cta-color underline mt-8">Read More</span>
            </div>
          </div>
        </nuxt-link>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',

  async asyncData({ $content, params}) {
    const posts = await $content('articles', params.slug)
      .only(['title', 'description', 'img', 'slug', 'date', 'read', 'tag'])
      .sortBy('createdAt', 'asc')
      .fetch();
    
    return{
      posts
    }
  }
}
</script>

<style>

  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  html{
    overflow-x: hidden;
  }

  body{
    position: relative;
    font-family: 'Nunito', sans-serif;
    background-color: #010713;
    color: #DAE6FF;

    padding-top: 1rem;
    padding-left: 4rem;
    padding-right: 4rem;
    padding-bottom: 1rem;
  }

  .logo{
    max-width: 5rem;
  }

  

  .post_featured_image{
    max-width: 10rem;
    border: 2px solid #00A1FF;
    border-radius: 5px;
  }

  /* .post_details_data span{
    
  } */

  .hero_section p{
    max-width: 60ch;
  }

  /* .hero_section_circle_blur{
    
  } */

  .bg_img{
    top: 55%;
  }
  
</style>
