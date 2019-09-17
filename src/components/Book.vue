<template>
  <div>
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img v-bind:src="book.portada" alt="book image" style="width:300px;height:400px;" />
      </div>
      <div class="flip-card-back">
        <h2>{{ book.titulo }}</h2>
        <h4>{{ book.descripcion }}</h4>
        <button v-bind:href="book.portada" class="btn btn-primary" data-fancybox="images">More Info</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["book"]
};
</script>

<style scoped>
</style>