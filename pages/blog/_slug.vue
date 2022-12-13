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
