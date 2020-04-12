<template>
  <li class="list-group-item media" @click="onBookSelect">
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
      if (this.book.volumeInfo.imageLinks) {
        return this.book.volumeInfo.imageLinks.thumbnail
      } else {
        return 'No image'
      }
    },
    formatAuthors() {
      if (this.book.volumeInfo.authors) {
        return this.book.volumeInfo.authors.join(', ')
      } else {
        return 'No known author'
      }
    }
  },
  methods: {
    onBookSelect() {
      this.$emit('bookSelect', this.book)
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