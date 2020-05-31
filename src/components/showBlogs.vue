<template>
  <div v-theme:column.second.third="'wide'" id="show-blogs">
      <h1>All blog articles</h1>
      <input type="text" v-model="search" placeholder="Search blogs" >
        <div class="single-blog" v-for="(post, index) in filteredPosts" :key="index">
            <router-link :to="'/post/' + post.id"><h2 v-rainbow>{{ post.title | to-uppercase }}</h2></router-link>
            <article>{{ post.content | snippet }}</article>
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
      this.$http.get('https://vue-project-45a3e.firebaseio.com/posts.json')
        .then(data => {
            return data.json();
        }).then(data => {
            for(let key in data) {
                data[key].id = key;
                this.posts.push(data[key])
            }
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
