<template>
<div class="container">
    <article>
        <h1>{{post.title}}</h1>
        <p>{{post.content}}</p>
    </article>
    <aside>
        <h3>Post you might enjoy</h3>
        <ul>
            <li v-for="related in relatedPosts">
                <!-- <nuxt-link :to="`/posts/${related.id}`">{{related.title}}</nuxt-link> -->
                <nuxt-link :to="{ name: 'posts-id', params: {id: related.id} }">{{related.title}}</nuxt-link>
            </li>
        </ul>
    </aside>
</div>
    
</template>

<script>
export default {
    head() {
        return {
            title: this.post.title
        }
    },
    data(){
        return {
            id: this.$route.params.id,
        }
    },
    computed: {
        post() {
            return this.$store.state.posts.all.find(post => post.id === this.id)
        },
        relatedPosts() {
            return this.$store.state.posts.all.filter(post => post.id !== this.id)
        }
    }
}
</script>

<style>

</style>
