<template>
  <button> 
    <slot></slot>
  </button>
</template>
<script>
export default {
  name: 'my-button'
}
</script>
<style scoped>
   button{
    height: 40px;
    width: 100px;
    background-color: transparent;
    border: 1px solid teal;
    color: teal;
    margin-top: 10px;
    align-self: flex-end;
    cursor: pointer;
    border-radius: 2px;
  }
  button:hover{
    background: teal;
    color: #fff;
  }
</style>