<template>
  <ul class="list-group">
    <BookListItem 
      v-for="book in books" 
      :book="book"
      :key="book.id"
    >
    </BookListItem>
  </ul>
</template>

<script>
import BookListItem from './BookListItem'

export default {
  name: 'BookList',
  components: {
    BookListItem
  },
  props: ['books']
}
</script>

<style>

</style>