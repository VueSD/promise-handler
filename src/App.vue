<template>
  <div id="app">
    <p v-if="error" class="error">{{ error.message }}</p>

    {{ details }}
  </div>
</template>

<script>
export default {
  data: () => ({
    details: null,
    error: null
  }),

  async mounted() {
    try {
      this.details = await fetch(
        "https://jsonplaceholder.typicode.com/todos/1"
      ).then(res => res.json());
    } catch (error) {
      this.error = error;
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
  margin-top: 60px;
}

.error {
  color: red;
}
</style>
