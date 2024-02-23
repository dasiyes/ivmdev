<template>
  <div class="about">
    <h1>This is an about page</h1>
    <h3>Views</h3>
    <p>
      Views are the pages of your app and are the containers for the components. They are the entry point for the router and are where you should fetch data and pass it down to the components.
    </p>
    <h3>Styles</h3>
    <p>Under assets there the two global css files. base.css is for the css variables. These can be accessed from anywhere. main.css is for global styling classes. base.css is imported in main.css. All components and views should have scoped styling.  </p>
    <h3>Routing</h3>
    <p>pretty easy, just copy pasta the about example</p>
    <h3>State Management</h3>
    <p>
      The state management is done with pinia. It is a store that is reactive and can be accessed from anywhere. It is a lot like vuex but it is a lot more simple and has a lot less boilerplate.
      example in this component
    </p>
    <div>
    <h1>Example of state management</h1>
    <h1>Count: {{ count }}</h1>
    <button @click="increment">Increment</button>
    </div>

    <h3>Component state:</h3>
    <p>for a variable to be reactive in the template it needs to be reactive -> use ref()</p>
    <p>also all pinia variable imported like count are refs, so in script use count.value</p>
    <h2>{{ bool1 }}</h2>
    <button @click="flipBool1">Flip bool1</button>
    <h2>{{ bool2 }}</h2>
    <button @click="flipBool2">Flip bool2</button>

  </div>
  
 

</template>

<script setup lang="ts">
import { useExampleStore } from '@/stores/example';
import { storeToRefs } from 'pinia';
import { ref } from 'vue'

const eStore = useExampleStore()
const { count  } = storeToRefs(eStore)
const {increment} = eStore

let bool1 = true
const bool2 = ref(true)

const flipBool1 = () => {
  bool1 = !bool1
}

const flipBool2 = () => {
  bool2.value = !bool2.value
}

</script>

<style scoped>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}
</style>
