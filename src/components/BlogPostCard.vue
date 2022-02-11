<template>
    <div class="blog_post_card">
        <h2>Submitted by: {{blog_post[2]}}</h2>
        <h4>{{blog_post[1]}}</h4>
        <h6>{{blog_post[3]}}</h6>

    </div>
</template>

<script>
    export default {
        name: 'blog-post-card',
        props: {
            blog_post: Array
        },
    }
</script>

<style scoped>
.blog_post_card {
    display: grid;
    place-items: center;
    border: .7px black solid;
    padding: 0px 30px;
    width: 80%;
}
</style>