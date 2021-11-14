<template>
 <li>
    <div>
      <strong>{{post.id}}.&nbsp;Название {{post.title}}</strong>
      <hr/>
      <p>{{post.body}}</p>
    </div>
    <my-button 
      style="width: 70px; height: 20px;"
      @click="this.$emit('removePost', post.id)"
      class="red"
    >
      Delete
    </my-button>    
  </li>
</template>
<script>
export default {
  props: {
    post: {
      type: Object,
      required: true
    },
    index: Number
  },
  methods: {
    removePost(id){
      console.log(id);
      this.$emit('removePost', id)
    }
  }
}
</script>
<style >
  li{
    display: flex !important;
    justify-content: space-between;
    align-items: center !important;
    margin-bottom: 10px;
    padding: 5px;
    border: 1px solid teal;
  }
  button{
    margin: 0;
  }
</style>