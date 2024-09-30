<template>
  <div class="PostView">
    <div class="container mx-auto my-8">
      <header v-if="post" class="text-center mb-8">
        <img
          :src="post.imageUrl"
          alt="Post Cover Image"
          class="w-full h-64 object-cover mb-6 rounded-lg"
        />
        <h1 class="text-4xl font-semibold mb-2">{{ post.title }}</h1>
        <p class="text-gray-600">By {{ post.author }} on {{ formatDate(post.createdAt) }}</p>
      </header>

      <!-- Post Content -->
      <article v-if="post" class="bg-white shadow-md rounded-lg p-6 mb-8">
        <div v-html="post.content" class="prose prose-lg"></div>
      </article>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'PostView',
  data() {
    return {
      post: null,
      loading: true,
      error: false,
      errorMessage: ''
    }
  },
  methods: {
    async fetchPost() {
      const postId = this.$route.params.id
      try {
        const postResponse = await axios.get(`http://localhost:3000/posts/${postId}`)
        this.post = postResponse.data
        this.loading = false
      } catch (error) {
        console.error(error)
        this.loading = false
        this.error = true
        this.errorMessage = 'An error occurred while fetching the post.'
      }
    },
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString(undefined, options)
    }
  },
  mounted() {
    this.fetchPost()
  }
}
</script>

<style scoped>
/* Additional styles can be added here */
.prose {
  max-width: none; /* Allow full width for content */
}
</style>
