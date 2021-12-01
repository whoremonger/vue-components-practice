<template>

  <Greet name="Bruce" hero-name="Batman" />
  <Greet name="Clark" hero-name="Superman" /> <!-- props naming convention is to use - format for props 
  and camel case for javascript. Vue supports the conversion. Mke sure you stick to it throughout the project -->
  <Greet name="Diana" hero-name="Wonderwoman" />
  <Greet :name="name" :hero-name="channel" />
        
  <Article id="my-article" title="Article Title" :likes="50" :isPublished="true" /> <!-- to enforce that "like" 
  is a number or non-string value type v-bind it -->

<!-- No prop attriubutes are attributes that are calling in a component html tag that does not need to be 
declared in the props object examples are the "id" "class" and "style" attributes  -->

<!-- Props can only sent data from component to component in the same layer.... -->

<!--Provide/Inject make it so you can pass information directly to the end component 
without going throught the other layer components.
1. Provide the value in the App componment (main)
2. Inject the value in the last layer component 

"provide" is a property object in the App.js component
like "data() but to sent to the last layer component.

"inject" is a array underneath "name" in the export default that
 injects or recieved the data inside the target end component 'F' 
 
 To use the provide property in the App.js you have to use the "data()" property
 then bind it with a "this" keyword to it and Provide should be a provide() return fuction -->
  <h3>App.js Component username - {{ name2 }}</h3>
 <ComponentC />
 <!-- custom events/component events -->
 <!-- to make a event to another component use "emits" 
 property array in the component then call the custom event in template. To communicate 
 from child component to parent component -->

  <button @click="showPopup = true">Show Popup</button>
  <Popup v-show="showPopup" @close="closePopup" />

  <!-- Components and v-model -->
  <!--v- model doesnt know how to behave in a custom component. The data will be blank. -->
   
  <Input v-model="name3" />
  <!--slots -->

  <Card></Card> <!--Displays default content -->

  <Card>
    Card Content
  </Card>

  <Card>
    <h2>Card Content</h2>
  </Card>

  <Card>
    <img src="https://picsum.photos/200" />
  </Card>

  <Card>
    <template v-slot:header> <!--this is how you name slots -->
    <h3>Header</h3>
    </template> 
    <template v-slot:default> <!--default because the slot doesnt have a name -->
      <img src="https://picsum.photos/200" />
    </template>
    <template v-slot:footer>
      <button>View Details</button>
    </template>
  </Card>
<!-- use "v-slot" followed by the name of the slot to give access to "slotProps" 
to structure the data for props -->
  <NameList>
    <template v-slot:default="slotProps">
      {{ slotProps.firstName }} {{ slotProps.lastName }}
    </template>
  </NameList>

  <NameList>
    <template v-slot:default="slotProps">
      {{ slotProps.lastName }}, {{ slotProps.firstName }}
    </template>
  </NameList>

  <NameList>
    <template v-slot:default="slotProps">
      {{ slotProps.firstName }}
    </template>
  </NameList>


  <h4>App component text</h4>
 
  <ChildStyles>
    <h4>ChildStyles component text</h4>
  </ChildStyles> 

<!--Dynamic Components -->


  <button @click="activeTab ='TabA'">Tab A</button>
  <button @click="activeTab = 'TabB'">Tab B</button>
  <button @click="activeTab = 'TabC'">Tab C</button>

  <!--Vue specific html tag -->
  <!--use component tag with ":is=".when you need to switch between components (like tabs) Use "keep-alive" 
  tag to cache the component to any input data so it the component wont need to reload. Good for forms and to speed up performance-->
  <keep-alive>
  <component :is="activeTab" />
  </keep-alive>

  <!--
  <TabA v-if="activeTab === 'TabA'" />
  <TabB v-if="activeTab === 'TabB'" />
  <TabC v-if="activeTab === 'TabC'" />
  -->
<!--Teleport Components -->
  <teleport to="#portal-root"> <!--Built in component. "to" is where the component will teleport to.
  Good for modals that need to render outside the DOM so that the background is fuzzed out.
  Especially if the app.js has different global size requirements than the component needs.
  You can also cotinue to nest components into other components and the component is still the child component of App.js.
  Also the portaled component acts as a regular child of APP.js so to not have complex component layering.
   -->
    <Portal />
  </teleport>

</template>

<script>
import Greet from './components/Greet.vue'
import Article from './components/Article.vue'
import ComponentC from './components/ComponentC.vue'
import Popup from './components/Popup.vue'
import Input from './components/Input.vue'
import Card from './components/Card.vue'
import NameList from './components/NameList.vue'
import ChildStyles from './components/ChildStyles.vue'
import TabA from './components/TabA.vue'
import TabB from './components/TabB.vue'
import TabC from './components/TabC.vue'
import Portal from './components/Portal.vue'

export default {
  name: 'App',
  components: {
    Greet,
    Article,
    ComponentC,
    Popup,
    Input,
    Card,
    NameList,
    ChildStyles,
    TabA,
    TabB,
    TabC,
    Portal,
  },
  data() {
    return {
      name: 'Jarrad',
      name2: 'BullShitter',
      channel: 'The Dope Show', // you can also bind the data into prop from the data property. Use v-bind or ":".
      showPopup: false,
      name3: '',
      activeTab: 'TabA'
    }
  },
  methods: {
    closePopup(name) {
      this.showPopup = false
      console.log('name:', name)
    },
  },
  provide() {
    return {
      username: this.name2,
    }
  },
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h4{
  color: orange;
}
</style>
