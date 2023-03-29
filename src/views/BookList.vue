<template>
  <form @submit.prevent="searchBooks" class="search-box">
    <input type="text" placeholder="Search for a book" v-model="search" />
    <input type="submit" value="Search" />
  </form>
  <h1>Booklist</h1>
  <p>Total Book count: {{ $store.getters.getbooks.length }}</p>

  <BookTable :books="books" @book-update="toogleFavListEntry" />
</template>

<script>
import BookTable from "@/components/BookTable.vue";
import { mapGetters } from "vuex";

export default {
  data() {
    return { search: "" };
  },
  name: "BookList",
  components: {
    BookTable,
  },
  computed: {
    ...mapGetters({ books: "getfiltredbooks" }),
  },
  methods: {
    toogleFavListEntry(book) {
      this.$store.dispatch("toogleFavListEntry", book);
    },
    searchBooks() {
      this.$store.commit("SET_SEARCHQUERY", this.search);
    },
  },
};
</script>
<style scoped>
.search-box {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  border-radius: 10px;
}
</style>
