<template>
  <BookPage :bookListPage="this.apiBookList"/>
</template>

<script>
  import BookPage from './components/pages/BookPage.vue';

export default {
  name: "App",
  components: {
      BookPage,
  },
  data() {
    return {
      apiUri : "https://gustavo-api.gustavofreitas9.repl.co/book-api",
      apiBookList : [],
    }
  },
  methods: {
    async getBooks() {
      try {
        let response = await fetch(this.apiUri);
        this.apiBookList = await response.json();
      } catch(error) {
        console.error(error);
      }
    }
  },
  created() {
    this.getBooks();
  }
}
</script>

<style>
@import url("https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/css/bootstrap.min.css");

header {
line-height: 1.5;
}

.main-content {
  display: flex;
  flex-direction: column;
}

.logo {
display: block;
margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
header {
  display: flex;
  place-items: center;
  padding-right: calc(var(--section-gap) / 2);
}

.logo {
  margin: 0 2rem 0 0;
}

header .wrapper {
  display: flex;
  place-items: flex-start;
  flex-wrap: wrap;
}
}
</style>
