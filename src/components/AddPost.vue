<template>
  <form @submit.prevent="addPost">
    <my-input 
      v-model="title"
      placeholder="Название..."
    />
    <my-input 
      v-model="body"
      placeholder="Информация..."
    />
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
      this.show = false
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

</style>