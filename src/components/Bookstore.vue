<template>
  <div>
    <div v-if="loading" id="spinner"></div>
    <h1
      v-if="getBooks.length==0 && myarr.length>0 "
      id="message"
    >No Books Match your search criteria</h1>
    <div id="display" class="row d-flex justify-content-center">
      <div class="flip-card" v-for="(book,i) in getBooks" :key="i">
        <Book :book="book"></Book>
      </div>
    </div>
  </div>
</template>

<script>
import Book from "./Book.vue";

export default {
  name: "bookstore",
  components: {
    Book
  },
  props: ["searchInput"],

  data() {
    return {
      myarr: [],
      loading: false
    };
  },
  methods: {
    getData() {
      this.loading = true;
      fetch("https://api.myjson.com/bins/1h3vb3", {
        method: "GET"
      })
        .then(function(responce) {
          console.log(responce);
          return responce.json();
        })
        .then(print => {
          this.loading = false;
          this.myarr = print.books;
          console.log(this.myarr);
        })
        .catch(function(err) {
          this.loading = false;
          console.log(err);
        });
    }
  },
  computed: {
    getBooks() {
      return this.myarr.filter(book =>
        book.titulo.toUpperCase().includes(this.searchInput.toUpperCase())
      );
    }
  },
  created() {
    this.getData();
  }
};
</script>

<style scoped>
#display {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  width: 80%;
  margin: auto;
}

.flip-card {
  grid-column: span 4;
}

@media screen and (max-width: 480px) {
  .flip-card {
    grid-column: span 12;
  }
}

/* SPINNER */

#spinner {
  visibility: visible;
  width: 80px;
  height: 80px;

  border: 2px solid #f3f3f3;
  border-top: 3px solid #f25a41;
  border-radius: 100%;

  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;

  animation: spin 1s infinite linear;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>