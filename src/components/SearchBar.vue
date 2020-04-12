<template>
  <div>
    <h3>Find books</h3>
    <input class="searchbar" @input="onInput" type="text" />
    <div class="form-check form-check-inline">
      <input class="form-check-input" @click="onRadioClick" type="radio" id="title" value="title" name="search-filter" checked />
      <label class="form-check-label" for="title">Title</label>
    </div>
    <div class="form-check form-check-inline">
      <input class="form-check-input" @click="onRadioClick" type="radio" id="author" value="author" name="search-filter" />
      <label class="form-check-label" for="title">Author</label>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data () {
    return {
      searchTerm: null,
      searchFilter: 'title'
    }
  },
  methods: {
    onInput(event) {
      this.searchTerm = event.target.value
      this.$emit("termChange", this.searchTerm, this.searchFilter)
    },
    onRadioClick(event) {
      this.searchFilter = event.target.value
      this.$emit("termChange", this.searchTerm, this.searchFilter)
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