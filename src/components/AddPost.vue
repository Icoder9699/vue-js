<template>
  <form @submit.prevent="addPost">
    <input v-model="title" type="text" placeholder="Название">
    <input v-model="body" type="text" placeholder="Текст">
    <my-button type="submit">создать</my-button>
  </form>
</template>
<script>
export default {
  methods:{
    addPost(){
      if(this.title === '' || this.body === ''){
        return
      }
      const newPost = {
        title: this.title,
        body: this.body,
        id: Date.now()
      }
      this.$emit('addPostHandler', newPost)
      this.title = ''
      this.body = ''
    }
  },
  data(){
    return {
      title: '',
      body: ''
    }
  }
}
</script>
<style scoped>
  form{
    display: flex;
    flex-direction: column;
  }
  input {
    height: 40px;
    margin-top: 10px;
    padding: 5px;
    outline: none;
    border: 2px solid teal;
  }
 
</style>