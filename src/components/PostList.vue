<template>
 <ul> 
    <post-item
      v-for="(post, i) in posts"
      :post="post"
      :key="i"
      :index="i"
      @removePost="removePost"
    />
  </ul>
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