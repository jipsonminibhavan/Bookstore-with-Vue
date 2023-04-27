<template>
  <header class="header">
    <section class="header__section">
      <p class="header__task-name">📚📖 B👀KSTORE📖📚</p>
      <div>
        <nav class="nav justify-content-center">
          <router-link to="/new-book">New Book</router-link>|
          <router-link to="/book-list">Booklist</router-link>|
          <router-link :to="{ name: 'fav-list' }">Favorite</router-link>|
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
  background: linear-gradient(to bottom right, #9be15d, #00e3ae);
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
</style>
