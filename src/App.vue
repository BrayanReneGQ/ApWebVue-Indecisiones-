<template>

          <!-- 

  <img alt="Vue logo" src="./assets/logo.png">
 
    <Counter titulo ="Entraron !!!"  />

      <Counter v-bind:start="110"/>
           -->   
           <indecision/>

</template>

<script>

import Counter from './components/Counter.vue'
import Indecision from './components/Indecision.vue'

export default {
  name: 'App',
  components:{
    //Counter,
    Indecision,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #460101;
  margin-top: 60px;
}
</style>
