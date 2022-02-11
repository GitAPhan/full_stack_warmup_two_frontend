<template>
  <div>
    <p>{{ get_status_message }}</p>
    <blog-post-card
      v-for="blog_post in blog_posts"
      :key="blog_post.id"
      :blog_post="blog_post"
    ></blog-post-card>
  </div>
</template>

<script>
import axios from "axios";
import BlogPostCard from "@/components/BlogPostCard.vue";

export default {
  name: "blog-post",
  components: {
    BlogPostCard,
  },
  data() {
    return {
      blog_posts: [],
      get_status_message: undefined,
    };
  },
  mounted() {
    // get request to grab all posts
    axios
      .request({
        url: "http://localhost:5000/blog",
      })
      .then((res) => {
        this.blog_posts = res.data;
      })
      .catch((err) => {
        this.get_status_message = err.response.data;
      });
  },
};
</script>

<style scoped>
</style>