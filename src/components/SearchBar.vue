<template>
  <div class="searchbar-container">
    <input class="searchbar" @input="onInput" type="text" placeholder="Search here" />
    <div class="form-search-filter">
      <div class="form-check form-check-inline">
        <input class="form-check-input" @click="onRadioClick" type="radio" id="title" value="title" name="search-filter" checked />
        <label class="form-check-label" for="title">Title</label>
      </div>
      <div class="form-check form-check-inline form-search-author">
        <input class="form-check-input" @click="onRadioClick" type="radio" id="author" value="author" name="search-filter" />
        <label class="form-check-label" for="title">Author</label>
      </div>
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
      if (this.searchTerm) {
        this.$emit("termChange", this.searchTerm, this.searchFilter)
      }
    }
  }
};
</script>

<style scoped>
  .searchbar-container {
    display: flex;
    align-items: center;
  }
  .searchbar {
    font-size: 18px;
    padding: 10px;
    width: 75%;
    max-height: 5vh;
  }
  div {
    text-align: center;
    margin: 20px;
  }
  .form-search-author {
    margin-left: -5px;
  }
</style>