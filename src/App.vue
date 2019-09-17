<template>
  <div>
    <vHeader v-on:headerToApp="onSearchInput($event)"></vHeader>
    <Bookstore v-bind:searchInput="searchInput"></Bookstore>
  </div>
</template>

<script>
import vHeader from "./components/Header.vue";
import Bookstore from "./components/Bookstore.vue";

export default {
  name: "app",
  components: {
    vHeader,
    Bookstore
  },
  data() {
    return {
      searchInput: "" // This value is set to the value emitted by the child
    };
  },
  methods: {
    onSearchInput(value) {
      this.searchInput = value;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.flip-card {
  margin: 10px;
  background-color: transparent;
  width: 300px;
  height: 400px;
  perspective: 1000px; /* Remove this if you don't want the 3D effect */
  box-shadow: 6px 4px 5px 0px rgba(0, 0, 0, 0.2);
}

/* This container is needed to position the front and back side */
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front,
.flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
  background-color: #bbb;
  color: black;
}

/* Style the back side */
.flip-card-back {
  background-color: #ccffff;
  color: #4d485f;
  transform: rotateY(180deg);
}

button {
  width: 40%;
  margin-top: auto;
  margin: auto;
  font-size: 1em;
  padding: 10px;
  background-color: #2fa9c2;
  border: 1px solid #2fa9c2;
  border-radius: 5px;
}

h2,
h4 {
  margin: 15px;
}
h4 {
  font-size: 1.2em;
}
</style>
