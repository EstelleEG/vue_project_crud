<template>
  <div class="form">
    <div class="form-input">
      <label for="name">Name of the book</label>
      <input type="text" v-model="book.name">
    </div>

    <div class="form-input">
      <label for="image">URL Image</label>
      <input type="text" v-model="book.imageURL">
    </div>

    <div class="form-input"> 
      <label for="author">Author name</label>
      <input type="text" v-model="book.author">
    </div>

    <div class="form-input">
      <label for="author">Collection</label>
      <input type="text" v-model="book.collection">
    </div>

    <div class="form-input"> 
      <label for="author">ISBN number</label>
      <input type="text" v-model="book.ISBN">
    </div>

    <div class="form-input">
      <label for="author">Volume</label>
      <input type="text" v-model="book.volume">
    </div>

    <div class="form-input"> 
      <label for="author">Designation</label>
      <input type="text" v-model="book.designation">
    </div>

    <div>
    <button @click="newBook" class="btn-form">Add book</button></div>

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
    async newBook() {
      await axios.post(
        'http://picwebloire.fr/estelle/back/api/create.php',
        {
          id: this.book.id,
          name: this.book.name,
          author: this.book.author,
          collection: this.book.collection,
          ISBN: this.book.ISBN,
          dimensions: this.book.volume,
          designation: this.book.designation,
          imageURL: this.book.imageURL,
        }
      )
      await this.$router.push({ name: 'list' });
    },
  },
}
</script>

<style scoped>

.form-input{
  display: flex;
  flex-direction: column;
  justify-content: center;
  width:80%;
  margin-bottom: 5em;
  padding: 12px 20px;
  margin: 8px auto;
  box-sizing: border-box;
}

.btn-form{
  background-color: royalblue;
  border: none;
  color: white;
  padding: 16px 32px;
  text-decoration: none;
  margin: 4px 2px;
  cursor: pointer;
}
  
</style>