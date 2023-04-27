<template>
  <SearchBar />
  <h1>Booklist</h1>
  <p>Total book count: {{ $store.getters.getbooks.length }}</p>

  <BookTable :books="books" @book-update="toogleFavListEntry" />
</template>

<script>
import BookTable from "@/components/BookTable.vue";
import SearchBar from "@/components/SearchBar.vue";
import { mapGetters } from "vuex";

export default {
  data() {
    return { search: "" };
  },
  name: "BookList",
  components: {
    BookTable,
    SearchBar,
  },
  computed: {
    ...mapGetters({ books: "getfiltredbooks" }),
  },
  methods: {
    toogleFavListEntry(book) {
      this.$store.dispatch("toogleFavListEntry", book);
    },
  },
};
</script>
<style scoped>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}
html {
  font-size: 62.5%;
  box-sizing: border-box;
}

.search-box {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  border-radius: 10px;
}
</style>
