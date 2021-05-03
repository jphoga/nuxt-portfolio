<template>
  <article>
    <h1 id="about-title">{{ page.title }}</h1>
    <p id="about-subtitle">...{{ page.description }}</p>
    <nuxt-content :document="page" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const page = await $content('about').fetch()

    return {
      page,
    }
  },
}
</script>

<style>
@import url('https://emoji-css.afeld.me/emoji.css');

#about-title {
  font-size: 56px;
}

#about-subtitle {
  margin-top: -8px;
  margin-bottom: 32px;
}

h1 {
  font-weight: bold;
}

h2 {
  margin-top: 2rem;
}

article {
  margin: 4rem 24rem;
}

img {
  width: 39rem;
}
</style>
