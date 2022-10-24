<template>
    <article>
        <nuxt-content :document="article" />
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

<style scoped>

.nuxt-content{
    display: grid;
    place-content: center;padding-top: 1rem;
    padding-left: 2rem;
    padding-right: 2rem;
    padding-bottom: 1rem;
}

.nuxt-content h1{
    font-size: 2rem;
}

@media (min-width: 500px){
    .nuxt-content{
      padding-top: 1rem;
      padding-left: 4rem;
      padding-right: 4rem;
      padding-bottom: 1rem;
    }
}


</style>