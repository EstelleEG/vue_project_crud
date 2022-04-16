<template>
  <table class="styled-table">
    <thead>
    <tr>
      <th>Id</th>
      <th>Name</th>
      <th>Author</th>
      <th>Actions</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="book in books" :key="book.id">
      <td>{{ book.id }}</td>
      <td>{{ book.name }}</td>
      <td>{{ book.author }}</td>
      <td>
        <i class="fas fa-eye" @click="goToBookDetails(book.id)"></i>
        <i class="fas fa-pen" @click="editBook(book.id)"></i>
        <i class="fas fa-trash" @click="deleteBook(book.id)"></i>
      </td>
    </tr>
    <!-- and so on... -->
    </tbody>
  </table>
</template>

<script>
import axios from "axios";

export default {
  name: "DatatableComponent",
  props:['books'],
  methods:{
    goToBookDetails(bookId) {
      this.$router.push({name: 'details', params: {bookId: bookId}})
    },
    editBook(bookId) {
      this.$router.push({name: 'edit', params: {bookId: bookId}})
    },
    async deleteBook(bookId){

      await axios.post('http://picwebloire.fr/estelle/back/api/delete.php', {
        action: 'delete',
        id: bookId
      })
      this.$emit('deleteBook', bookId)
    }
  }
}
</script>

<style scoped>
.styled-table {
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  font-size: 0.9em;
  font-family: sans-serif;
  min-width: 800px;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.15);
}

.styled-table thead tr {
  background-color: royalblue;
  color: #ffffff;
}

.styled-table th,
.styled-table td {
  padding: 12px 15px;
}

.styled-table tbody tr {
  border-bottom: 1px solid #dddddd;
}

.styled-table tbody tr:nth-of-type(even) {
  background-color: #f3f3f3;
}

.styled-table tbody tr:last-of-type {
  border-bottom: 2px solid royalblue;
}

.styled-table tbody tr.active-row {
  font-weight: bold;
  color: royalblue;
}
</style>