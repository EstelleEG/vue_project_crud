<template>
  <div class="home">
    <img alt="Vue logo" src="@/assets/imgs/books.jpg">
    <HelloWorld msg=""/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>

<style> 
.home img {
  width:40rem;
  border-radius: 50%;
}
</style>
