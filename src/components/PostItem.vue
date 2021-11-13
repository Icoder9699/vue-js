<template>
 <li>
    <p>
      <strong>{{index + 1}}.&nbsp;Название {{post.title}}&nbsp;</strong>
      {{post.body}}
    </p>
    <my-button @click="this.$emit('removePost', post.id)">Delete</my-button>    
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
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
    padding: 5px;
    border: 1px solid teal;
    height: 40px;
    display: flex;
    align-items: center;
  }
</style>