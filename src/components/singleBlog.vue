<template>
    <div>
        <p v-show="loading">Loading...</p>

        <div v-show="!loading" id="single-blog">
            <h1>{{ blog.title }}</h1>
            <article>{{ blog.content }}</article>
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
        this.$http.get('https://vue-project-45a3e.firebaseio.com/posts/' + this.id + '.json')
            .then(data => {
                return data.json();
            }).then(data => {
                this.blog = data;
                this.loading = false
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