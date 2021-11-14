<template>
  <div class="container">
    <h1>Todo Application</h1>
    <my-button 
      style="margin-top: 10px"
      @click="showModal"
    >
      Создать пост
    </my-button>
    <modal 
      v-model:show="modalVisible"
    >
      <add-post
        @addPostHandler="addPost"
      />
    </modal>
    <select v-model="selectedSort">
      <option value="all">Все</option>]
      <option value="title">По названию</option>]
      <option value="body">По текст</option>]
    </select>
    <post-list
      v-if="!isLoading"
      :posts="posts"
      @removePost="removePostHandler"
    />
    <h2 v-else>Загрузка...</h2>
  </div>
</template>
<script>
import PostList from './components/PostList'
import AddPost from './components/AddPost'
import Modal from './components/Modal'
import axios from 'axios'
export default {
  components: {
    PostList, AddPost, Modal
  },
  data(){
    return{
      posts: [],
      modalVisible: false,
      isLoading: true,
      selectedSort: 'all'
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
    },
    async fetchData(){
        const resp = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10?_sort=' + this.selectedSort)
        console.log(resp.data);
        this.posts = resp.data
        this.isLoading = false
    }
  },
  watch: {
    selectedSort(newValue){
      this.fetchData(newValue)
    }
  },
  mounted(){
    this.fetchData()
  },
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
  select{
    display: block;
    width: 100%;
    height: 40px;
    margin: 10px 0;
  }
</style>