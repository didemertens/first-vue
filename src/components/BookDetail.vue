<template>
  <div v-if="book" class="col-md-8">
    <div class="details">
      <h4>{{ book.volumeInfo.title }}</h4>
      <p>{{ book.volumeInfo.description }} </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BookDetail',
  props: ['book']
}
</script>

<style scoped>
  .details {
    margin-top: 10px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>