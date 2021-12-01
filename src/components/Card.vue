<template>
  <div class="card">
    <!--Slots make it so you cant add more data than a prop like a picture or html tags
    Inseat of making a prop use html tags "<slot> </slot>" in the template. in the App.js 
    the component html uses an opening and closing tag instead -->

    <!--Named slots - when you have multiple slots. Can can leave one slot unnamed -->
    <div id="card-header">
      <slot name="header"></slot>

    </div>
    <div id="card-content">
      <slot></slot>

    </div>
    <div id="card-footer">
      <slot name="footer"></slot>

    </div>

  </div>
</template>

<script>

  export default {
    name: 'Card', 
  }
  
</script>

<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  padding: 16px;
  margin-bottom: 20px;
  width: 200px;
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

</style>