<template>
  <body>
    <h1>{{ book.title }}</h1>
    <p>{{ book.abstract }}</p>
    <p>{{ book.price }}</p>
    <p>{{ book.author }}</p>
    <img :src="book.cover" alt="" />
    <a href="/book-list">Back</a>
  </body>
</template>

<script>
export default {
  data() {
    return {
      book: {},
    };
  },
  async created() {
    /* const response = await fetch(
      "http://localhost:4730/books/" + this.$route.params.id
    );
    const bookData = await response.json();
    this.book = bookData;*/
    this.book = this.$store.getters.getbooks.find((book) => {
      return this.$route.params.id === book.id;
    });
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

body {
  padding: 5rem 5rem 10rem;
  line-height: 1.7;
  font-family: "Nunito Sans", sans-serif;
  color: #555;
  min-height: 100vh;
  background: linear-gradient(to bottom right, #9be15d, #00e3ae);
}
</style>
