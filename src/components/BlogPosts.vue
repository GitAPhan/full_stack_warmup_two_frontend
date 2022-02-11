<template>
  <div class="blog_posts">
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
  methods: {
    update_post(payload) {
      this.blog_post.unshift(payload);
    },
  },
  mounted() {
    this.$root.$on("newPost", this.update_post);

    // get request to grab all posts
    axios
      .request({
        url: "https://randomapiupload.ml/api/blog",
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
.blog_posts {
  display: grid;
  place-items: center;
  row-gap: 10px;
  border: black solid 1px;
}
</style>