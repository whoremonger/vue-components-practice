<template>
<!-- Components and Props -->

<!-- vbase-css for the vue snippets extension creates a clean component template -->
  <div>
    <h2>Hello, {{ name }} A.K.A. {{ heroName }}</h2> <!-- //then "bind" the prop, in javascript inside the component use camelcase
    and inthe app.js main component use "-" case for the prop name inside the component html tag as a naming convention-->
  </div>
</template>

<script>
  export default {
    name: 'Greet',
    props: ['name', 'heroName'],  //props are the data a component tag can accept, it is an array
  }
</script>

<style scoped>

</style>