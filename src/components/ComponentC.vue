<template>
  <h2>Component C</h2>
  <ComponentE />
</template>

<script>
import ComponentE from './ComponentE'
export default {
  name: 'CompononentC',
  components: {
    ComponentE,
  },
}
</script>

<style scoped>

</style>