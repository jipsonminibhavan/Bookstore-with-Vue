<template>
  <div class="grid gap-3">
    <h1>Add a New Book</h1>
    <form class="row g-3">
      <div class="col-md-4">
        <label class="lh-lg">Title</label>
        <input
          class="form-control form-control-lg"
          v-model="book.title"
          type="text"
          placeholder="Add a booktitle"
        />
      </div>
      <div class="col-md-4">
        <label class="lh-lg">Subtitle</label>
        <input
          class="form-control form-control-lg"
          v-model="book.subtitle"
          type="text"
          placeholder="Add a subtitle"
        />
      </div>
      <div class="col-md-4">
        <label class="lh-lg">ISBN</label>
        <input
          class="form-control form-control-lg"
          v-model="book.isbn"
          type="text"
          placeholder="Add an ISBN"
        />
      </div>
      <div class="col-12">
        <label class="lh-lg">Abstract</label>
        <textarea
          class="form-control w-75 p-3"
          v-model="book.abstract"
          type="text"
          placeholder="Add an abstract"
          rows="3"
        ></textarea>
      </div>
      <div class="col-md-3">
        <label class="lh-lg">Author</label>
        <input
          class="form-control form-control-lg"
          v-model="book.author"
          type="text"
          placeholder="Add an author"
        />
      </div>
      <div class="col-md-3">
        <label class="lh-lg">Publisher</label>
        <input
          class="form-control form-control-lg"
          v-model="book.publisher"
          type="text"
          placeholder="Add a publisher"
        />
      </div>

      <div class="col-md-3">
        <label class="lh-lg">Cover</label>
        <input
          class="form-control form-control-lg"
          v-model="book.cover"
          img
          :src="book.cover"
          alt=""
        />
      </div>
      <div class="col-md-2">
        <label class="lh-lg"> price</label>
        <input
          class="form-control form-control-lg"
          v-model="book.price"
          type="text"
          placeholder="Add a price"
        />
      </div>
      <div class="d-grid gap-2 lh-lg col-6 mx-auto">
        <button type="button" class="btn btn-primary" @click="addBook">
          Add Book
        </button>
      </div>
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

      fetch(`${process.env.VUE_APP_API_URL}/books`, {
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
