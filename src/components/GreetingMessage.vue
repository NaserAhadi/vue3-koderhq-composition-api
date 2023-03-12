<template>
  <p v-if="!fullName.length>1">here is Greeting!</p>
  <p v-else>hello => {{ fullName }}</p><br>
  <button @click="toggleMenuFromChild">toggle menu from child</button>
  <p>here is injected item: {{ uName }}</p>
</template>

<script>
import {computed, inject} from 'vue'

export default {
  name: 'GreetingMessage',
  props: {
    firstName: {
      type: String,
      default: ''
    },
    lastName: {
      type: String,
      default: ''
    }
  },
  emits:['toggleMenu'],
  setup(props,context){
    const fullName = computed(() => {
      return `${props.firstName} ${props.lastName}`
    })

    function toggleMenuFromChild(){
      context.emit('toggleMenu')
    }

    const uName= inject('username')
    return {fullName, toggleMenuFromChild, uName}
  }
}
</script>

<style scoped>

</style>
