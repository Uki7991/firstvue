<template>
  <div v-theme:column.second.third="'wide'" id="show-blogs">
      <h1>All blog articles</h1>
        <div class="single-blog" v-for="(post, index) in posts" :key="index">
            <h2 v-rainbow>{{ post.title | to-uppercase }}</h2>
            <article>{{ post.body | snippet }}</article>
        </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
        posts: []
    }
  },
  methods: {
  },
  created() {
      this.$http.get('https://jsonplaceholder.typicode.com/posts')
        .then(data => {
            console.log(data)
            this.posts = data.body.slice(0, 10);
        })
  },
}
</script>

<style>
#show-blogs{
    max-width: 800px;
    margin: 0px auto;
}
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;
}
</style>
