<template>
  <div id="app">
    {{ details }}
  </div>
</template>

<script>
export default {
  data: () => ({
    details: null
  }),

  async mounted() {
    this.details = await fetch(
      "https://jsonplaceholder.typicode.com/todos/1"
    ).then(res => res.json());
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
  margin-top: 60px;
}
</style>
