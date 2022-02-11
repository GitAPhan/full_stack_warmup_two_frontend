<template>
  <div id='app'>
    <blog-posts></blog-posts>
    <blog-post-form></blog-post-form>
  </div>
</template>

<script>
import BlogPosts from "@/components/BlogPosts.vue";
import BlogPostForm from "@/components/BlogPostForm.vue";


    export default {
        components: {
          BlogPosts,
          BlogPostForm,
        },
    }
</script>

<style>
</style>
