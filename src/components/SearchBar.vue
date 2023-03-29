<template>
  <form @submit.prevent="searchBooks" class="search-box">
    <input
      type="text"
      class="d-flex justify-content-center"
      placeholder="Search for a book"
      v-model="search"
    />
    <input class="btn btn-primary" type="submit" value="Search" />
  </form>
</template>

<script>
export default {
  methods: {
    searchBooks() {
      this.$store.commit("SET_SEARCHQUERY", this.search);
    },
  },
};
</script>
