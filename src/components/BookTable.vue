<template>
  <table class="table table align-middle table-responsive table-hover">
    <thead>
      <tr>
        <th scope="col">Bookname</th>
        <th scope="col">Author</th>
        <th scope="col">ISBN</th>

        <th scope="col">&nbsp;</th>
      </tr>
    </thead>
    <tbody class="table-group-divider grid gap-0 column-gap-3">
      <tr v-for="book of books" :key="book.id">
        <td class="p-2 g-col-6">{{ book.title }}</td>
        <td class="p-2 g-col-6">{{ book.author }}</td>
        <td class="p-2 g-col-6">{{ book.isbn }}</td>
        <td class="p-2 g-col-6">
          <slot class="p-2 g-col-6">
            <router-link
              class="p-3"
              :to="{ name: 'book-detail', params: { id: book.id } }"
              >Details</router-link
            >
            <FavButton
              class="p-3"
              :is-active="book.isFav"
              @clicked="updateBook(book)"
            />
          </slot>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import FavButton from "@/components/FavButton.vue";

export default {
  components: {
    FavButton,
  },

  props: {
    books: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    updateBook(book) {
      this.$emit("book-update", book);
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

tbody,
thead {
  padding: 5rem 5rem 10rem;
  line-height: 1.7;
  font-family: "Nunito Sans", sans-serif;
  color: #555;
  min-height: 100vh;
  background: linear-gradient(to bottom right, #9be15d, #00e3ae);
}
</style>
