<template>
  <div id='app'>
    <blog-post-form></blog-post-form>
    <blog-posts></blog-posts>
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
