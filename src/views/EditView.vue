<template>
  <div>
    <input type="text" v-model="book.name">

    <input type="text" v-model="book.author">

    <input type="text" v-model="book.collection">

    <input type="text" v-model="book.ISBN">

    <input type="text" v-model="book.dimensions">

    <input type="text" v-model="book.designation">

    <div @click="saveBook">SAVE</div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "EditView",
  data() {
    return {
      book: {}
    }
  },

  methods: {
    saveBook() {
      axios.post('http://localhost:8000/api/update.php', JSON.stringify({
        book: this.book
      }))
    },
  },

  async created() {
    const { bookId } = this.$route.params
    console.log(bookId)
    const apiDetailsUri = 'http://localhost:8000/api/single_read.php/?id=' + bookId
    const oneBook = await axios.get(apiDetailsUri)
    this.book = oneBook.data
  }
}
</script>

<style scoped>

</style>