<template>
  <div class="PostView">
    <div class="container mx-auto my-8">
      <header class="text-center mb-8">
        <h1 class="text-4xl font-semibold mb-2">{{ post.title }}</h1>
        <p class="text-gray-600">By {{ post.author }} on {{ post.date }}</p>
      </header>

      <!-- Post Content -->
      <article class="bg-white shadow-md rounded-lg p-6 mb-8">
        <div v-html="post.content" class="prose prose-lg"></div>
      </article>

      <!-- Navigation for Previous and Next Posts -->
      <div class="flex justify-between mb-6">
        <router-link
          v-if="prevPost"
          :to="`/posts/${prevPost.id}`"
          class="text-blue-500 hover:text-blue-700 transition duration-300"
        >
          &larr; Previous Post: {{ prevPost.title }}
        </router-link>
        <router-link
          v-if="nextPost"
          :to="`/posts/${nextPost.id}`"
          class="text-blue-500 hover:text-blue-700 transition duration-300 text-right"
        >
          Next Post: {{ nextPost.title }} &rarr;
        </router-link>
      </div>

      <!-- Comments Section -->
      <section class="comments">
        <h2 class="text-2xl font-semibold mb-4">Comments</h2>
        <div v-for="comment in comments" :key="comment.id" class="bg-gray-100 p-4 mb-4 rounded">
          <p class="font-bold">{{ comment.author }}</p>
          <p class="text-gray-700">{{ comment.content }}</p>
        </div>
        <div class="mt-6">
          <h3 class="text-xl font-semibold mb-2">Leave a Comment</h3>
          <textarea
            v-model="newComment"
            rows="4"
            class="w-full border border-gray-300 rounded p-2 mb-4"
            placeholder="Write your comment..."
          ></textarea>
          <button
            @click="addComment"
            class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600 transition duration-300"
          >
            Submit
          </button>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PostView',
  data() {
    return {
      post: {
        title: 'Sample Post Title',
        author: 'Author Name',
        date: 'September 26, 2024',
        content:
          '<p>This is where the post content goes. It can include <strong>HTML</strong> tags.</p>'
      },
      comments: [
        { id: 1, author: 'Commenter 1', content: 'Great post!' },
        { id: 2, author: 'Commenter 2', content: 'Thanks for sharing!' }
      ],
      newComment: '',
      prevPost: { id: 1, title: 'Previous Post Title' },
      nextPost: { id: 3, title: 'Next Post Title' }
    }
  },
  methods: {
    addComment() {
      if (this.newComment.trim()) {
        const newCommentObj = {
          id: this.comments.length + 1,
          author: 'You',
          content: this.newComment
        }
        this.comments.push(newCommentObj)
        this.newComment = '' // Reset comment field
      }
    }
  }
}
</script>

<style scoped>
/* Additional styles can be added here if needed */
.prose {
  max-width: none; /* Allow full width for content */
}
</style>
