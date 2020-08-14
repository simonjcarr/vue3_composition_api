<template>
  <div class="mx-4 rounded bg-gray-400 shadow">
    <div class="p-2">
      <div class="font-bold">Latest Posts</div>
    </div>
    <div class="bg-white p-2 border-2 border-gray-400 ">
      <div v-for="post in posts" :key="post.id">
        <div class="mb-2">- <router-link :key="`/post/${post.id}`" :to="`/post/${post.id}`">{{ post.title }}</router-link></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: []
    };
  },
  methods: {
    fetchPosts() {
      fetch("https://jsonplaceholder.typicode.com/posts")
        .then(response => response.json())
        .then(data => (this.posts = data.slice(-10)));
    }
  },
  mounted() {
    this.fetchPosts();
  }
};
</script>

<style></style>
