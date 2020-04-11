<template>
  <li class="list-group-item">
    <img :src="thumbnailURL" :alt="book.volumeInfo.title" />
    {{ book.volumeInfo.title }}
    -
    {{ formatAuthors }}
  </li>
</template>

<script>
export default {
  name: 'BookListItem',
  props: ['book'],
  computed: {
    thumbnailURL() {
      return this.book.volumeInfo.imageLinks.thumbnail
    },
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