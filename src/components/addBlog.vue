<template>
  <div id="add-blog">
    <h2>Add new blog post</h2>
    <form v-if="!submitted">
        <label for="">Blog title:</label>
        <input type="text" v-model.lazy="blog.title" required>
        <label for="">Blog content: </label>
        <textarea name="" required id="" v-model.lazy="blog.content" cols="30" rows="10"></textarea>
        <div id="checkboxes">
            <label for="">Ninjas</label>
            <input type="checkbox" value="ninjas" v-model="blog.categories">
            <label for="">Wizards</label>
            <input type="checkbox" value="Wizards" v-model="blog.categories">
            <label for="">Mario</label>
            <input type="checkbox" value="mario" v-model="blog.categories">
            <label for="">Cheese</label>
            <input type="checkbox" value="cheese" v-model="blog.categories">
        </div>
        <label>Author:</label>
        <select v-model="blog.author">
            <option v-for="(author, index) in authors" :key="index">{{ author }}</option>
        </select>
        <button v-on:click.prevent="post">Add Blog</button>
    </form>
    <div v-if="submitted">
        <h3>Thanks for adding your post</h3>
    </div>
    <div id="preview">
        <h3>Preview Blog</h3>
        <p>Blog title: {{ blog.title }}</p>
        <p>Blog content: <pre>{{ blog.content }}</pre></p>
        <p>Blog categories: </p>
        <ul>
            <li v-for="(item, index) in blog.categories" :key="index">{{ item }}</li>
        </ul>
        <p>Author: {{ blog.author }}</p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  },
  data() {
    return {
        blog: {
            title: '',
            content: '',
            categories: [],
            author: ''
        },
        authors: ['The Net Ninja', 'The Angular Avenger', 'The Vue Vindicator'],
        submitted: false
    }
  },
  methods: {
      post() {
          this.$http.post('https://jsonplaceholder.typicode.com/posts', {
              title: this.blog.title,
              body: this.blog.content,
              userId: 1
          }).then(data => {
              console.log(data)
              this.submitted = true
          })
      }
  }
}
</script>

<style scoped>
#add-blog *{
    box-sizing: border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 10px;
}
#checkboxes label{
    display: inline-block;
}
</style>
