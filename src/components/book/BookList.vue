<script>
import BookCard from './BookCard.vue';
import axios from "axios";
import { store } from "../../data/store";

export default {
  data() {
    return {
      title: "Books List",
      store,
    };
  },

  components: { BookCard, },

  methods: {
    fetchBooks(uri = store.baseUrl + "books") {
      axios.get(uri).then((response) => {
        store.books = response.data.data;
        store.pagination.links = response.data.links;
      });
    },
  },

  created() {
    this.fetchBooks();
  },
};
</script>

<template>
  <h1>{{ title }}</h1>
  <div class="row row-cols-3 g-3">
    <div class="col" v-for="book in store.books">
      <BookCard  :book="book"/>
    </div>
</div>
<nav class="my-4" aria-label="Page navigation example">
  <ul class="pagination">
    <li
      v-for="link in store.pagination.links"
      @click="fetchBooks(link.url)"
      class="page-item"
    >
      <a class="page-link" href="#" v-html="link.label"></a>
    </li>
  </ul>
</nav>
</template>

<style lang="scss" scoped></style>
