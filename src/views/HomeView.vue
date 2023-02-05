<template>
  <div class="home">
   home
   <p ref="p">My name is {{name}} and my age is {{age}}</p>
   <button @click="handleClick">click me</button>
   <button @click="age ++">add 1 to age</button>
   <input type="text" v-model="name">
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'


export default {
  name: 'HomeView',
  setup(){
console.log('setup')
const p = ref(null)
const name = ref( 'Mario')
const age = ref(30)

const handleClick = () => {
  name.value = 'Lue'
  age.value = 35
  console.log(p,p.value)
 // p.value.classList.add('test')
 // p.value.textContent = 'hi all'
}
return{name: name, age: age, handleClick, p}
  } 
}
</script>
