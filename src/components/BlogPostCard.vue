<template>
    <div>
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

</style>