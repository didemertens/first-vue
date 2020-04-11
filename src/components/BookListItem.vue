<template>
  <li>
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
      let formattedAuth = ''
      if (this.book.volumeInfo.authors) {
        formattedAuth = this.book.volumeInfo.authors.join(', ')
      }
      return formattedAuth 
    }
  }
}
</script>