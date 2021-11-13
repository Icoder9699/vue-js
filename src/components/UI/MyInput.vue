<template>
  <input 
    type="text"
    :value="modelValue"
    @input="onChange"
  />
</template>
<script>
export default {
  name: 'my-input',
  props: {
    modelValue: [String, Number],
    placeHolder: String
  },
  methods: {
    onChange(event){
      this.$emit('update:modelValue', event.target.value)
    }
  },
  mounted(){
    console.log(this.props)
  }
}
</script>
<style scoped>
  input {
    height: 40px;
    margin-top: 10px;
    padding: 5px;
    outline: none;
    border: 2px solid teal;
  }
</style>