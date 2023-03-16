<template>
  <header class="header">
    <section class="header__section">
      <p class="header__task-name">📚📖👀 Bookstore</p>
      <div class="header__bootcamp-info-wrapper">
        <nav class="nav justify-content-center">
          <router-link to="/new-book">New Book</router-link>|
          <router-link to="/book-list">Booklist</router-link>|
          <router-link :to="{ name: 'fav-list' }">Favoriten</router-link>|
        </nav>
      </div>
    </section>
  </header>

  <router-view />
</template>
<script>
export default {
  async created() {
    await this.$store.dispatch("loadBooks");
  },
};
</script>
<style scoped>
.header {
  background-color: rgb(29, 237, 199);
  color: #fff;
  text-align: center;
  margin-bottom: 40px;
}
.header__task-name {
  font-size: 50px;

  margin: 0;
}
.header__section {
  padding: 10px 10px;
}
</style>
