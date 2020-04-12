<template>
  <div>
    <div class="jumbotron">
      <h1>Find books</h1>
    </div>
    <div class="container">
      <SearchBar @termChange="onTermChange"></SearchBar>
      <div class="row">
        <BookList @bookSelect="onBookSelect" :books="books"></BookList>
        <BookDetail :book="selectedBook"></BookDetail>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import SearchBar from './components/SearchBar'
import BookList from './components/BookList'
import BookDetail from './components/BookDetail'

const booksKey = process.env.VUE_APP_BOOKS_KEY

export default {
  name: 'App',
  components: {
    SearchBar,
    BookList,
    BookDetail
  },
  data() {
    return {
      books: [],
      selectedBook: null
    }
  },
  methods: {
    onTermChange(searchTerm, searchFilter) {
      axios.get(`https://www.googleapis.com/books/v1/volumes?q=in${searchFilter}:${searchTerm}&key=${booksKey}`)
      .then(response => this.books = response.data.items)
    },
    onBookSelect(book) {
      this.selectedBook = book
    }
  }
}
</script>

<style scoped>
  .jumbotron {
    background-color: rgb(245, 245, 245);
    text-align: center;
  }
</style>