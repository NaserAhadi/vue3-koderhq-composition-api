<template>
  <p v-if="!fullName.length>1">here is Greeting!</p>
  <p v-else>hello => {{ fullName }}</p><br>
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
  setup(props){
    const fullName = computed(() => {
      return `${props.firstName} ${props.lastName}`
    })

    return {fullName}
  }
}
</script>

<style scoped>

</style>
