<template>
  <main>
    <div class="blog-container">
      <TheHeader />

      <h1 class="blog-header">Blog Posts</h1>
      <ul class="blog-card-container">
        <li v-for="article of articles" :key="article.slug" class="blog-card">
          <NuxtLink
            :to="{ name: 'blog-slug', params: { slug: article.slug } }"
            class="blog-card-link"
          >
            <img
              v-if="article.img"
              class="blog-card-image"
              :src="article.img"
            />

            <div class="blog-card-box">
              <h2 class="blog-card-box-header">{{ article.title }}</h2>
              <p>by {{ article.author.name }}</p>
              <p class="blog-card-box-text">
                {{ article.description }}
              </p>
            </div>
          </NuxtLink>
        </li>
      </ul>

      <h3 class="topics">Topics</h3>
      <ul class="topic">
        <li v-for="tag of tags" :key="tag.slug" class="topic-item">
          <NuxtLink :to="`/blog/tag/${tag.slug}`" class="">
            <p class="topic-link">
              {{ tag.name }}
            </p>
          </NuxtLink>
        </li>
      </ul>
      <footer class="footer">
        <p class="footer-text">
          Created by
          <a href="https://twitter.com/debs_obrien" class="footer-link"
            >Debbie O'Brien</a
          >
          at NuxtJS. See the
          <a
            href="https://nuxtjs.org/blog/creating-blog-with-nuxt-content"
            class="footer-link"
            >tutorial</a
          >
          for how to build it.
        </p>
      </footer>
    </div>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content('articles', params.slug)
      .only(['title', 'description', 'img', 'slug', 'author'])
      .sortBy('createdAt', 'desc')
      .fetch()
    const tags = await $content('tags', params.slug)
      .only(['name', 'description', 'img', 'slug'])
      .sortBy('createdAt', 'asc')
      .fetch()
    return {
      articles,
      tags,
    }
  },
}
</script>

<style class="postcss">
.blog-container {
  margin: 0 8rem;

  /* display: flex; */

  /* justify-content: space-between; */

  /* align-items: center; */

  /* flex-direction: row; */

  /* flex-wrap: wrap; */
}
</style>
