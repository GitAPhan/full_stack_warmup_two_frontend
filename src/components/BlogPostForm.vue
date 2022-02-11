<template>
  <div class="blog_post_form">
    <h1>Submit New Blog Post</h1>
    <form :key="unique_key" class="blog_post_form" action="javascript:void(0)">
      <input type="text" placeholder="username" ref="username" />
      <input type="text" placeholder="content" ref="content" class="content_form" />
      <p>{{ post_status_message }}</p>
      <input type="submit" @click="post_blog" />
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "blog-post-form",
  data() {
    return {
      post_status_message: undefined,
      unique_key: 4107513,
    };
  },
  methods: {
    post_blog() {
      var username = this.$refs.username.value;
      var content = this.$refs.content.value;

      axios
        .request({
          url: "https://randomapiupload.ml/api/blog",
          method: "POST",
          data: {
            username: username,
            content: content,
          },
        })
        .then((res) => {
          this.unique_key++;
          this.post_status_message = res.data.message;
          var post = [res.data.id, content, username, res.data.created_at]
          this.$root.$emit('newPost', post)
        })
        .catch((err) => {
          this.unique_key++;
          this.post_status_message = err.response.data;
        });
    },
  },
};
</script>

<style scoped>
.blog_post_form {
    display: grid;
}

.content_form {
    height: 75px;
}

input {
    text-align: center;
}
</style>