<template>
  <div class="main_container">
    <header class="w-full flex justify-between items-center">
      <img class="logo" src="https://ik.imagekit.io/u33i3sss0/Portfolio_Website/android-chrome-512x512_exmBxaGLK.png?ik-sdk-version=javascript-1.4.3&updatedAt=1665675785139" alt="logo">
      <!-- <nav>
        <a href="#">About me</a>
        <a href="#">Contact</a>
      </nav> -->
      <a class="pt-3 pb-3 pr-5 pl-5 bg-transparent border-4 border-cta-color rounded-full" href="https://yudaicreator.com">Portfolio</a>
    </header>
    <section class="hero_section">
      <h1 class="text-9xl">Hero</h1>
    </section>

    <section class="posts">
      <div class="post" v-for="post of posts" :key="post">
        <nuxt-link :to="{name: 'slug', params: {slug: post.slug}}">
          <img :src="`${post.img}`" alt="">
          <div class="post_details_wrapper">
            <div class="post_details">
              <h3>{{post.title}}</h3>
              <p>{{post.description}}</p>
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
      .only(['title', 'description', 'img', 'slug'])
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

  body{
    font-family: 'Nunito', sans-serif;
    background-color: #010713;
    color: #DAE6FF;

    padding: 2rem;
  }

  .logo{
    max-width: 5rem;
  }
  
</style>
