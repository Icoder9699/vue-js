<template>
  <div class="modal" v-show="show" @click="hideModal">
    <div class="modal__container" @click.stop>
      <button class="close" @click="hideModal">&times;</button>
      <slot></slot>
    </div>
  </div>
</template>
<script>
export default {
  props: ['show'],
  methods: {
    hideModal(){
      this.$emit("update:show", false)
    }
  }
}
</script>
<style>
  .modal{
    top: 0;
    left: 0;
    bottom:0 ;
    right:0;
    position: fixed;
    background: rgb(0, 0, 0, 0.5);
    display: flex;
  }
  .modal__container{
    position: relative;
    margin: auto;
    width: 500px;
    min-height: 100px;
    background: #fff;
    border-radius: 20px;
    padding: 20px;
  }
  .close {
    position: absolute;
    top: -10px;
    right: -5px;
    background: red;
    font-size: 20px;
    border: none;
    color: #fff;
    cursor: pointer;
    border: 1px solid red;
    border-radius: 50px;

  }
</style>