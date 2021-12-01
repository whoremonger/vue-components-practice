<template>
  <h2>Component F</h2>
  <h3>Component F username from App.js - {{ username }}</h3>
</template>

<script>
export default {
  name: 'ComponentF',
  inject: ['username'],
    
}
</script>

<style scoped>

</style>