<template>
  <div
    class="px-8 mx-auto mt-12 prose sm:px-6 md:px-4 lg:px-2 xl:px-0 xl:prose-xl lg:prose-lg md:prose-md"
  >
    <h2>{{ post.title }}</h2>
    <p>{{ post.description }}</p>
    <nuxt-content :document="post" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params: { slug } }) {
    const post = await $content('blog', slug).fetch()
    return {
      post,
    }
  },
}
</script>

<style>
.img {
  display: block;
  margin: 0 auto;
  /* center */
  max-width: 100%; /* prevent images from becoming distorted */
  border: 1px solid black; /* add a border around images */
  box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5); /* add a drop shadow */
  background-image: linear-gradient(
    to bottom,
    white,
    lightgray
  ); /* add a background gradient */
  filter: grayscale(100%); /* apply a grayscale effect */
}
</style>
