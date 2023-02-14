<template>
  <div class="home">
   home
  
  </div>
</template>

<script>
import { ref, reactive } from '@vue/reactivity'



export default {
  name: 'HomeView',
  setup(){
const posts = ref([
  {title:'welcome to the blog', body:'Lorem ipsum', id:1},
  {title:'top 5 CSS tips', body:'Lorem ipsum', id:2},
])
  
    

return{posts}
  } 
}

</script>
