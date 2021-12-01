<template>
  <div>
    <h2>This is a popup</h2> <!--$emit('name of event', 'data to pass') -->
    <input type="text" v-model="name" />
    <button @click="$emit('close', name)">Close popup</button>
  </div>
  
</template>

<script>
//use "emits" property and "$emit()" function in the template to use a component event
  export default {
    name: 'Popup',
    emits: {
      close:  (name) => {
        if(!name) {
          return false
        } else {
          return true
        }
      }
    },
    data() {
      return {
      }   
    },
  }
   
</script>

<style scoped>

</style>