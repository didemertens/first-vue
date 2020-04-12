<template>
  <div>
    <h3>Find books</h3>
    <input class="searchbar" @input="onInput" type="text" />
    <input @click="onRadioClick" type="radio" id="title" value="title" name="search-filter" checked />
    <label for="title">Title</label>
    <input @click="onRadioClick" type="radio" id="author" value="author" name="search-filter" />
    <label for="title">Author</label>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data () {
    return {
      searchFilter: 'title'
    }
  },
  methods: {
    onInput(event) {
      this.$emit("termChange", event.target.value, this.searchFilter)
    },
    onRadioClick(event) {
      this.searchFilter = event.target.value
    }
  }
};
</script>

<style scoped>
  .searchbar {
    width: 75%;
  }
  div {
    text-align: center;
    margin: 20px;
  }
</style>