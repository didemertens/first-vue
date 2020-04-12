<template>
  <div v-if="book">
    {{ book.volumeInfo.title }}
  </div>
</template>

<script>
export default {
  name: 'BookDetail',
  props: ['book']
}
</script>