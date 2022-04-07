<template>
  <div>
    <input type="text" v-model="book.name">

    <input type="text" v-model="book.author">

    <input type="text" v-model="book.collection">

    <input type="text" v-model="book.ISBN">

    <input type="text" v-model="book.dimensions">

    <input type="text" v-model="book.designation">

    <div @click="newBook">NEW</div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "NewBook",
  data() {
    return {
      book: {}
    }
  },

  methods: {
    newBook() {
      axios.post('http://localhost:8000/api/create.php', JSON.stringify({
        book: this.book
      }))
    },
  },
}



</script>

<style scoped>

</style>