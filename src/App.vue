<template>
  <!-- <p>{{ greetingMsg }} {{ greetingUser }}</p> -->
  <!-- <p>{{ greeting }}</p> -->
  <!-- <p><button @click="newGreetingOne">Regular Function</button></p>
  <p><button @click="newGreetingTwo">Anonymous Function</button></p>
  <p><button @click="newGreetingThree">Arrow Function</button></p> -->
  <!-- <p>{{ greeting }}</p>
  <input type="text" placeholder="first-name" @input="setFirstName"/>
  <input type="text" placeholder="las-name" @input="setLastName"/>  -->
  <GreetingMessage :first-name="user.firstName" :last-name="user.lastName" @toggleMenu="toggleShowMenu"/>

  <p>Hello {{ user.firstName }} {{ user.lastName }}</p>
  <input type="text" placeholder="first-name" v-model="user.firstName"/>
  <input type="text" placeholder="last-name" v-model="user.lastName"/> 
  <p>message is  here: {{ message }}</p>
  <input type="text" placeholder="message" v-model="message"/><br>

  <ul v-show="isShowMenu">
    <li>vue</li>
    <li>pwa</li>
    <li>javascript</li>
  </ul>
</template>

<script>
import {ref,computed, watch, provide} from 'vue'
import GreetingMessage from './components/GreetingMessage.vue'

export default {
  name: 'App',
  components: {
    GreetingMessage
  },
  setup(){
    // console.log('setup');
    // const greeting = ref({msg: 'hello', user: 'john'})
    // const greeting = ref('hello world')
    // setTimeout(() => {
    //   // change ref value
    //   greeting.value.msg = 'greetings'
    //   greeting.value.user = 'Naser'
    // }, 3000)
    // function newGreetingOne() {
    //   greeting.value = 'hello regular function'
    // }

    // const newGreetingTwo = function(){
    //   greeting.value = 'hello anonymous function'
    // }

    // const newGreetingThree = () => {greeting.value = 'hello arrow function'}
    const user = ref({firstName:'', lastName:''})
    function setFirstName($event){
      user.value.firstName = $event.target.value
    }

    function setLastName($event){
      user.value.lastName = $event.target.value
    }
    const greeting = computed(() => {
      return `Hello Dear ${user.value.firstName} ${user.value.lastName}`
    })

    const message = ref('')

    watch(message, (newValue, oldValue) => {
      console.log('newValue', newValue)
      console.log('oldValue', oldValue)
    }, {immediate: true})


    const isShowMenu = ref(true)
    function toggleShowMenu(){
      isShowMenu.value =! isShowMenu.value
    }

    provide('username', 'NaserAhadi')

    return {
      greeting, 
      // newGreetingOne, 
      // newGreetingTwo, 
      // newGreetingThree
      user,
      setFirstName,
      setLastName,
      message,
      isShowMenu,
      toggleShowMenu
    }
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
