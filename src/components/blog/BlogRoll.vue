<template>
  <div class="text-4xl font-bold mb-4">My Blog Roll</div>
  <div v-for="post in posts" :key="post.id">
    <div class="bg-gray-200 mb-4 shadow p-2 rounded">
      <div class="text-2xl font-semibold">
        <router-link :to="`/post/${post.id}`">{{ post.title }}</router-link>
      </div>
      <div class="mt-2 bg-gray-400 p-2 text-gray-700 rounded">
        {{ post.body }}
      </div>
    </div>
  </div>
</template>

<script>
import usePosts from "@/composables/blog/posts";
import { onMounted } from "vue";
export default {
  setup() {
    const { posts, fetchPosts } = usePosts();
    onMounted(() => fetchPosts());
    return { posts };
  }
};
</script>

<style></style>
