<template>
  <div>
    <div class="jumbotron jumbotron-fluid">
      <div class="container header-container">
        <h1>Find books</h1>
        <SearchBar @termChange="onTermChange"></SearchBar>
      </div>
    </div>
    <div class="container">
      <div v-if="books.length > 0" class="row">
        <BookList @bookSelect="onBookSelect" :books="books"></BookList>
        <BookDetail :book="selectedBook"></BookDetail>
      </div>
      <div v-else>
        <h5>Search for a book above!</h5>
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
    background-image: url("https://static.standard.co.uk/s3fs-public/thumbnails/image/2020/03/02/15/wpf-longlist-main.jpg");
    text-align: center;
    height: 45vh;
  }
  .header-container {
    margin-top: -5vh;
  }
</style>