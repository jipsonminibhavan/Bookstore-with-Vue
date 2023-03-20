<template>
  <header class="header">
    <section class="header__section">
      <p class="header__task-name">📚📖 B👀kstore📖📚</p>
      <div>
        <nav class="nav justify-content-center">
          <router-link to="/new-book">New Book</router-link>|
          <router-link to="/book-list">Booklist</router-link>|
          <router-link :to="{ name: 'fav-list' }">Favoriten</router-link>|
        </nav>
      </div>
    </section>
  </header>
  <form @submit.prevent="SearchBooks()" class="search-box">
    <input type="text" placeholder="Search for a book" v-model="search" />
    <input type="submit" value="Search" />
  </form>
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
  background-color: rgb(103, 231, 208);
  color: hsl(0, 0%, 5%);
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
.search-box {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  border-radius: 10px;
}
</style>
