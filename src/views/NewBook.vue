<template>
  <div class="about">
    <h1>Add a New Book</h1>
    <form>
      <div class="field">
        <label>Title</label>
        <input v-model="book.title" type="text" placeholder="Add a booktitle" />
      </div>
      <div class="field">
        <label>Subtitle</label>
        <input
          v-model="book.subtitle"
          type="text"
          placeholder="Add asubtitle"
        />
      </div>
      <div class="field">
        <label>isbn</label>
        <input v-model="book.isbn" type="text" placeholder="Add an ISBN" />
      </div>
      <div class="field">
        <label>Abstract</label>
        <input
          v-model="book.abstract"
          type="text"
          placeholder="Add an abstract"
        />
      </div>
      <div class="field">
        <label>Author</label>
        <input v-model="book.author" type="text" placeholder="Add an author" />
      </div>
      <div class="field">
        <label>publisher</label>
        <input
          v-model="book.publisher"
          type="text"
          placeholder="Add a publisher"
        />
      </div>
      <div class="field">
        <label> price</label>
        <input v-model="book.price" type="text" placeholder="Add a price" />
      </div>
      <div class="field">
        <label>Cover</label>
        <input v-model="book.cover" img :src="book.cover" alt="" />
      </div>
      <button type="button" class="btn btn-primary" @click="addBook">
        Add Book
      </button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      book: {
        title: "",
        subtitle: "",
        isbn: "",
        abstract: "",
        author: "",
        publisher: "",
        price: "$",
        cover: "http://….png",
      },
    };
  },
  methods: {
    addBook(event) {
      event.preventDefault();

      fetch("http://localhost:4730/books/", {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(this.book),
      })
        .then((res) => res.json)
        .then((data) => console.log(data));
    },
  },
};
</script>
