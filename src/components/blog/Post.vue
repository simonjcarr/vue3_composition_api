<template>
  <div>
    <div class="text-4xl font-bold">{{ post.title }}</div>
    <div>{{ post.body }}</div>
    <div class="italic mt-4">
      Author: <span class="text-red-500">{{ user.name }}</span>
    </div>
  </div>
</template>

<script>
import usePosts from "@/composables/blog/posts";
import router from "@/router";
export default {
  setup() {
    const { currentRoute } = router;
    const { fetchPost, post, user } = usePosts();
    fetchPost(currentRoute.value.params.id);
    return { post, user };
  }
};
</script>

<style></style>
