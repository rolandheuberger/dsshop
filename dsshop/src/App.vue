<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from "./components/layout/Header"

export default {
    name: "app",
    components: {
      Header
    }  
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
  color: #333;
}

.btn {
  border: none;
  background-color: hsl(200, 100%, 45%);
  color: #fff;
  padding: 0.5em 1em;
  transition: background-color 0.3s ease-in-out;
  cursor: pointer;
}

.btn:hover {
  background-color: hsl(200, 100%, 25%);
}
</style>
