
<template>
<!--Prop Types and Validations -->

  <div>
    <h2>Article Component</h2>
    <h2 v-bind="$attrs">{{ title }}</h2> <!-- then bind the prop -->
    <h2>Likes - {{ likes }}</h2>
    <h2>Published - {{ isPublished ? 'Yes' : 'No' }}</h2>
  </div>
  <!-- if you take the div wrapper out there will be no id added to the tags -->
  <!-- the $attrs bind adds the non prop attributes. only to that component tag -->
</template>

<script>
  export default {
    name: 'Article',
    props: { 
      title: {
          
        type: String, 
        required: true, //gives warning in browser that the component is required
        default: 'Article Default Title' //if there is no prop in html component then the default value will be shown instead
      },
      likes: Number,
      isPublished: Boolean, 
        //prop name and data type (gives warning to you if the type is wrong. Good for error checking.)
    },     //can do ojects too in props property
    inheritAttrs: false,  //prevents non prop attributes (id, style, or class) from being applied from the root element

  }
</script>

<style scoped>

</style>