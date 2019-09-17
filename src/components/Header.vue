<template>
  <div>
    <header>
      <div>
        <img class="logo" src="../../images/Logo.png" alt="ubiqum store image" srcset />
      </div>
      <div>
        <input
          v-model="value"
          v-on:keyup="sendInputValue"
          id="search"
          type="text"
          placeholder="Search for a book.."
        />
      </div>
    </header>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: ""
    };
  },
  name: "vHeader",
  methods: {
    sendInputValue() {
      this.$emit("headerToApp", this.value);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.logo {
  width: 400px;
  height: 100px;
}

header {
  display: flex;
  justify-content: center;
  padding: 15px;
  background-color: #2fa9c2;
  margin-bottom: 20px;
}

header div {
  align-self: center;
  padding: 0px 20px;
}

input {
  padding: 10px 50px;
  width: auto;
  border: 2px solid #4d485f;
  border-radius: 5px;
}
</style>
