<template>
  <div>
    <slot></slot>
  </div>
</template>

<script> //"scoped" means that that the styles are scoped only to the
//component. By default the app.js styles apply to all the components unless specified.
//"With scoped, the parent component's styles will not leak into child components. However,
//a child component's root node will be affected by both the parent's scoped CSS and the child's
// scoped CSS. This is by design so that the parent can style the child root element for
//layout purposes." If you dont want this use CSS modules.

//When using slots the parent components styles are applied and not the
// child component styles even though the content is embedded inside
//the child component.
  export default {
    name: 'ChildStyles',
  }
</script>

<style scoped>
h4 {
  color: olivedrab;
}

</style>