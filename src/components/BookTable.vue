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
