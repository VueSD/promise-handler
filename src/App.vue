<template>
  <div id="app">
    <h1>My App:</h1>

    <AsyncAwait :promise="request">
      <div slot-scope="data">
        <pre>{{ data }}</pre>
      </div>
    </AsyncAwait>
  </div>
</template>

<script>
import AsyncAwait from "@/components/AsyncAwait";

export default {
  components: {
    AsyncAwait
  },

  data: () => ({
    text: "hello world",
    request: fetch("https://jsonplaceholder.typicode.com/todos/1")
      .then(res => res.json())
      .then(results => {
        return new Promise((res, rej) => {
          setTimeout(() => {
            console.log(rej);
            // rej(new Error("nah bro"));
            res(results);
          }, 1000);
        });
      })
  })
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
