<template>
  <article v-if="projectPost" class="main article">
    <h1 class="article-title">{{ projectPost.title }}</h1>
    <p class="mt-4">{{ projectPost.description }}</p>
    <img class="cover-image" :src="projectPost.cover" />
    <div class="block mt-8 mb-4" v-html="$md.render(projectPost.body)" />
    <div v-if="projectPost.gallery">
      <img v-for="image in projectPost.gallery" class="image" :key="image.id" :src="image" />
    </div>
    <div>
      <iframe
        width="100%"
        height="454"
        src="https://www.youtube.com/embed/Jse8QwN79_k"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      >
      </iframe>
    </div>
  </article>
</template>
<script>
export default {
  async asyncData({ params, payload }) {
    if (payload) return { projectPost: payload }
    else
      return {
        projectPost: await require(`~/assets/content/projects/${params.project}.json`),
      }
  },
}
</script>
