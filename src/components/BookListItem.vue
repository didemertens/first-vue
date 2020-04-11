<template>
  <li>
    <!-- {{ book.volumeInfo.imageLinks.smallThumbnail }} -->
    {{ book.volumeInfo.title }}
    -
    {{ formatAuthors }}
  </li>
</template>

<script>
export default {
  name: 'BookListItem',
  props: ['book'],
  data() {
    return {
      authors: ''
    }
  },
  computed: {
    formatAuthors() {
      if (this.book.volumeInfo.authors) {
        return this.book.volumeInfo.authors.join(', ')
      } else {
        return 'No known author'
      }
    }
  }
}
</script>