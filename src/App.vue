<template>
  <div class="container">
    <h1>Todo Application</h1>
    <add-post
      @addPostHandler="addPost"
    />
    <post-list
      :posts="posts"
      @removePost="removePostHandler"
    />

  </div>
</template>
<script>
import PostList from './components/PostList'
import AddPost from './components/AddPost'
export default {
  components: {
    PostList, AddPost
  },
  data(){
    return{
      posts: [
        {id: 1, title: 'Javascript', body: 'Мощный язык'},
        {id: 2, title: 'Javascript', body: 'Изучать легко!'},
        {id: 3, title: 'Javascript', body: 'Можно создать всё!'},
      ],
    }
  },
  methods: {
    removePostHandler(id){
      this.posts = this.posts.filter(p => p.id !== id)
    },
    addPost(post){
      this.posts.push(post)
    }
  }
}
</script>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
  .container{
    width: 500px;
    margin: 50px auto;
  }
  
</style>