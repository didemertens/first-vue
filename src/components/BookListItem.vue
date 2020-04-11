<template>
  <li class="list-group-item media">
    <img class="mr-3" :src="thumbnailURL" :alt="book.volumeInfo.title" />
    <div class="media-body">
      {{ book.volumeInfo.title }}
      -
      {{ formatAuthors }}
    </div>
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

<style scoped>
  li {
    display: flex;
    align-items: center;
    cursor: pointer;
  }
  li:hover {
    background-color: #eee;
  }
</style>