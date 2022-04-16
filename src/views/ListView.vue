<template>
  <DatatableComponent :books="books" @deleteBook="deleteBook"></DatatableComponent>
</template>

<script>
import axios from 'axios'
import DatatableComponent from "@/components/DatatableComponent";

export default {
  name: 'ListView',
  data: () => ({
    books: [],
  }),
  components: {DatatableComponent},
  methods: {
    deleteBook(bookId){
      let index = this.books.indexOf(bookId);
      this.books.splice(index, 1);
    }
  },
  async created() {
    const books = await axios.get("http://picwebloire.fr/estelle/back/api/read.php")
    this.books = books.data
    console.log(this.books)
    console.log('created')
  }
}
</script>


<style scoped>
@import '@/assets/css/style.css';


</style>
