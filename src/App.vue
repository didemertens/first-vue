<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <BookList @bookSelect="onBookSelect" :books="books"></BookList>
  </div>
</template>

<script>
import axios from 'axios'

import SearchBar from './components/SearchBar'
import BookList from './components/BookList'
const booksKey = process.env.VUE_APP_BOOKS_KEY

export default {
  name: 'App',
  components: {
    SearchBar,
    BookList
  },
  data() {
    return {
      books: []
    }
  },
  methods: {
    onTermChange(searchTerm) {
      axios.get(`https://www.googleapis.com/books/v1/volumes?q=intitle:${searchTerm}&key=${booksKey}`)
      .then(response => this.books = response.data.items)
    },
    onBookSelect(book) {
      console.log(book.volumeInfo)
    }
  }
}
</script>