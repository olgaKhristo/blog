<template>
  <div class="home">
   home
   <p ref="p">My name is {{name}} and my age is {{age}}</p>
   <button @click="handleClick">click me</button>
   <button @click="age ++">add 1 to age</button>
   <input type="text" v-model="name">
   <h2>reactive</h2>
   <p>{{ninjaTwo.name}} - {{ninjaTwo.age}}</p>
   <button @click="updateNinjaTwo">updete Ninjs Two</button>
   <p>{{nameS}}</p>
   <input type="text" v-model="search">
   <p> search term - {{search}}</p>
   <div v-for="name in matchingNameArr" :key="name">
   {{name}}
   </div>
   <button @click="click">stop watching</button>
  </div>
</template>

<script>
import { ref, reactive } from '@vue/reactivity'
import { computed, watch, watchEffect } from '@vue/runtime-core'


export default {
  name: 'HomeView',
  setup(){
    const search = ref(' ')
    const nameArr = ref(['mario', 'olga', 'john', 'jack', 'jill'])
    const stopWatch = watch(search, () => {
    console.log('watch function run')
    })
    const stopWachEffect = watchEffect(() => {
      console.log('watchEffect function', search.value)
    })
    const matchingNameArr = computed( () => {
      return nameArr.value.filter((name) => name.includes(search.value))
    })
    const nameS = computed(() =>{
      return 'shun'
    })
console.log('setup')
const p = ref(null)
const name = ref( 'Mario')
const age = ref(30)
const ninjaTwo = reactive({name: 'Liu', age: 35})


const handleClick = () => {
  stopWatch()
  stopWachEffect()
  name.value = 'Lue'
  age.value = 35
  console.log(p,p.value)
 // p.value.classList.add('test')
 // p.value.textContent = 'hi all'
}
const updateNinjaTwo = () => {
  ninjaTwo.age = 45
}

return{name: name, age: age, handleClick, p, ninjaTwo, updateNinjaTwo, nameS, nameArr, search, matchingNameArr}
  } 
}
</script>
