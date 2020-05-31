<template>
  <div v-theme:column.second.third="'wide'" id="show-blogs">
      <h1>List blog titles</h1>
      <input type="text" v-model="search" placeholder="Search blogs" >
        <div class="single-blog" v-for="(post, index) in filteredPosts" :key="index">
            <h2 v-rainbow>{{ post.title | to-uppercase }}</h2>
        </div>
  </div>
</template>

<script>
import searchMixin from '../mixins/searchMixin'

export default {
  data() {
    return {
        posts: [],
        search: ''
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
  computed: {
  },
  filters: {
      toUppercase(value) {
          return value.toUpperCase();
      }
  },
  directives: {
      rainbow: {
            bind(el, binding, vnode) {
                el.style.color = "#" + Math.random().toString().slice(2,8);
            }
      }
  },
  mixins: [searchMixin]
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
