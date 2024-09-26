<template>
  <div class="min-h-screen flex flex-col">
    <div class="container mx-auto flex-grow my-8">
      <header class="text-center">
        <h1 class="text-4xl font-semibold mb-2">Blog Site</h1>
        <p class="text-gray-600">Welcome to my blog site</p>
      </header>

      <!-- Navigation Bar -->
      <nav class="mt-6">
        <ul class="flex justify-center space-x-4">
          <li><router-link to="/" class="text-blue-500 hover:underline">Home</router-link></li>
          <li>
            <router-link to="/about" class="text-blue-500 hover:underline">About</router-link>
          </li>
          <li>
            <router-link to="/posts" class="text-blue-500 hover:underline">Posts</router-link>
          </li>
          <li>
            <router-link to="/contact" class="text-blue-500 hover:underline">Contact</router-link>
          </li>
        </ul>
      </nav>

      <!-- Blog Posts Section -->
      <section class="mt-8">
        <h2 class="text-2xl font-semibold mb-4">Latest Posts</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <article class="bg-white shadow-md rounded-lg p-4">
            <h3 class="text-xl font-bold mb-2">Blog Post Title 1</h3>
            <p class="text-gray-700 mb-4">
              A brief description of the first blog post goes here. This is a summary to attract
              readers.
            </p>
            <router-link to="/posts/1" class="text-blue-500 hover:underline">Read More</router-link>
          </article>
          <article class="bg-white shadow-md rounded-lg p-4">
            <h3 class="text-xl font-bold mb-2">Blog Post Title 2</h3>
            <p class="text-gray-700 mb-4">
              A brief description of the second blog post goes here. This is a summary to attract
              readers.
            </p>
            <router-link to="/posts/2" class="text-blue-500 hover:underline">Read More</router-link>
          </article>
          <article class="bg-white shadow-md rounded-lg p-4">
            <h3 class="text-xl font-bold mb-2">Blog Post Title 3</h3>
            <p class="text-gray-700 mb-4">
              A brief description of the third blog post goes here. This is a summary to attract
              readers.
            </p>
            <router-link to="/posts/3" class="text-blue-500 hover:underline">Read More</router-link>
          </article>
        </div>
      </section>
    </div>

    <!-- Footer -->
    <footer class="mt-8 py-4 bg-gray-800 text-white text-center">
      <p>&copy; 2024 Blog Site. All rights reserved.</p>
    </footer>
  </div>
</template>
