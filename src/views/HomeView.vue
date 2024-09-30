<template>
  <div class="min-h-screen flex flex-col">
    <div class="container mx-auto flex-grow my-8">
      <header class="text-center">
        <h1 class="text-4xl font-semibold mb-2">Blog Site</h1>
        <p class="text-gray-600">Welcome to my blog site</p>
      </header>

      <!-- Blog Posts Section -->
      <section class="mt-8">
        <h2 class="text-2xl font-semibold mb-4">Latest Posts</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <article v-for="post in posts" :key="post.id" class="bg-white shadow-md rounded-lg p-4">
            <img
              :src="post.imageUrl"
              alt="Post Thumbnail"
              class="w-full h-48 object-cover rounded-t-lg mb-4"
            />
            <h3 class="text-xl font-bold mb-2">{{ post.title }}</h3>
            <p class="text-gray-700 mb-4">{{ post.excerpt }}</p>
            <router-link :to="`/posts/${post.id}`" class="text-blue-500 hover:underline"
              >Read More</router-link
            >
          </article>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HomeView',
  data() {
    return {
      posts: [] // This will hold the blog posts
    }
  },
  async mounted() {
    try {
      // Fetch the posts from your backend
      const response = await axios.get('http://localhost:3000/posts')
      this.posts = response.data
    } catch (error) {
      console.error('Error fetching posts:', error)
    }
  }
}
</script>

<style scoped>
/* Add any additional styles here */
</style>
