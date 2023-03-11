<template>
  <p v-if="!fullName.length>1">here is Greeting!</p>
  <p v-else>hello => {{ fullName }}</p><br>
  <button @click="toggleMenuFromChild">toggle menu from child</button>
</template>

<script>
import {computed} from 'vue'

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
  setup(props,context){
    const fullName = computed(() => {
      return `${props.firstName} ${props.lastName}`
    })

    function toggleMenuFromChild(){
      context.emit('toggleMenu')
    }

    return {fullName, toggleMenuFromChild}
  }
}
</script>

<style scoped>

</style>
