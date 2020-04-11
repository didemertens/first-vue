<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
  </div>
</template>

<script>
import axios from 'axios'

import SearchBar from './components/SearchBar'
const booksKey = process.env.VUE_APP_BOOKS_KEY

export default {
  name: 'App',
  components: {
    SearchBar
  },
  methods: {
    onTermChange(searchTerm) {
      axios.get(`https://www.googleapis.com/books/v1/volumes?q=${searchTerm}&key=${booksKey}`)
      .then(response => console.log(response))
      console.log(booksKey)
      console.log(searchTerm)
    }
  }
}
</script>