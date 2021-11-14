<template>
 <ul v-if="posts.length"> 
    <post-item
      v-for="(post, i) in posts"
      :post="post"
      :key="i"
      :index="i"
      @removePost="removePost"
    />
  </ul>
  <h3 
    v-else 
    style="margin-top: 10px; text-align: center;"
  >
    Пока постов нет
  </h3>
</template>
<script>
import PostItem from './PostItem.vue';
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true
    }
  },
  data(){
    return{

  }
  },
  methods: {
    removePost(id){
      this.$emit('removePost', id)
    }
  }
}
</script>
<style scoped>
  
  ul{
    margin: 0;
    margin-top: 10px;
    padding: 0;
    list-style-type: none;
  }
 
</style>