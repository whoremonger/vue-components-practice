<template>
  <div>Tab C Content</div>
  <input type="text" v-model="name" />
</template>

<!--keeping dynamic compoments alive -->
<!--When i switch tabs the input info gets cleared. Component needs to be cached. -->

<script>
  export default {
    name: 'TabC',
   data() {
        return {
          name: '',
        } 
    },
  }
</script>

<style scoped>

</style>