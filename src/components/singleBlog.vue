<template>
    <div>
        <p v-show="loading">Loading...</p>

        <div v-show="!loading" id="single-blog">
            <h1>{{ blog.title }}</h1>
            <article>{{ blog.body }}</article>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            id: this.$route.params.id,
            blog: {},
            loading: true
        }
    },
    created() {
        this.$http.get('https://jsonplaceholder.typicode.com/posts/' + this.id)
            .then(data => {
                this.loading = false
                console.log(data)
                this.blog = data.body
            })
    }
}
</script>

<style scoped>
    #single-blog {
        max-width: 960px;
        margin: 0 auto;
    }
</style>