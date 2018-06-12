<template>
  <div id="app">
    <Todo />
  </div>
</template>

<script src="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-beta/js/materialize.min.js"></script>
<script>
import Todo from './components/Todo.vue'

export default {
  name: 'app',
  components: {
    Todo
  }
}
</script>

<style>
@import url('https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-beta/css/materialize.min.css');
@import url('https://fonts.googleapis.com/icon?family=Material+Icons');
@import url("https://use.fontawesome.com/releases/v5.0.13/css/all.css");

body {
  background-color: #EEEEEE;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  /* align-items: center; */
}
body, html {
  margin: 0;
  height: 100%;
}
#app {
    width: 50%;
}
</style>
