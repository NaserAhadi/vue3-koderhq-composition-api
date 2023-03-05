<template>
  <!-- <p>{{ greetingMsg }} {{ greetingUser }}</p> -->
  <p>{{ greeting }}</p>
  <p><button @click="newGreetingOne">Regular Function</button></p>
  <p><button @click="newGreetingTwo">Anonymous Function</button></p>
  <p><button @click="newGreetingThree">Arrow Function</button></p>
</template>

<script>
import {ref} from 'vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  setup(){
    // console.log('setup');
    // const greeting = ref({msg: 'hello', user: 'john'})
    const greeting = ref('hello world')
    // setTimeout(() => {
    //   // change ref value
    //   greeting.value.msg = 'greetings'
    //   greeting.value.user = 'Naser'
    // }, 3000)
    function newGreetingOne() {
      greeting.value = 'hello regular function'
    }

    const newGreetingTwo = function(){
      greeting.value = 'hello anonymous function'
    }

    const newGreetingThree = () => {greeting.value = 'hello arrow function'}

    return {greeting, newGreetingOne, newGreetingTwo, newGreetingThree}
  },
  created(){
    // console.log('created');
  },
  mounted(){
    // console.log('mounted');
  }
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
</style>
