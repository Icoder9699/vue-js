<template>
  <div class="container">
    <h1>Todo Application</h1>
    <my-button 
      style="margin-top: 10px"
      @click="showModal"
    >
      Создать пост
    </my-button>
    <modal v-model:show="modalVisible">
      <add-post
        @addPostHandler="addPost"
      />
    </modal>
    <post-list
      :posts="posts"
      @removePost="removePostHandler"
    />

  </div>
</template>
<script>
import PostList from './components/PostList'
import AddPost from './components/AddPost'
import Modal from './components/Modal'
export default {
  components: {
    PostList, AddPost, Modal
  },
  data(){
    return{
      posts: [
        {id: 1, title: 'Javascript', body: 'Мощный язык'},
        {id: 2, title: 'Javascript', body: 'Изучать легко!'},
        {id: 3, title: 'Javascript', body: 'Можно создать всё!'},
      ],
      modalVisible: false
    }
  },
  methods: {
    closeModal(){
      this.modalVisible = false
    },
    showModal(){
      this.modalVisible = true
    },
    removePostHandler(id){
      this.posts = this.posts.filter(p => p.id !== id)
    },
    addPost(post){
      this.posts.push(post)
      this.modalVisible = false
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