<template>
  <div class="container">
    <form v-on:submit.prevent="addTodo">
      <input type="text" placeholder="Enter a todo" v-model="todo" required minlength="3" v-on:click="clearEditing">
    </form>
    <ul class="collection">
      <li class="collection-item" v-for="(data, index) in todos" :key='index'>
        <a href="#" v-on:click="toggleEdit(index)" v-show="!isSelected(index)">{{ data.todo }}</a>
        <i class="fa fa-minus-circle" v-on:click="remove(index)" v-show="!isSelected(index)"></i>
        <input type="text" v-model="data.todo" v-show="isSelected(index)" v-on:keyup.enter="untoggleEdit()">
        <i class="fa fa-times-circle" v-show="isSelected(index)" v-on:click="untoggleEdit()"></i>
      </li>
    </ul>
    <p class="blue-text text-darken-2">Total: <span class="badge">{{ todos.length }}</span></p>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  data() {
    return {
      todo: '',
      todos: [
          { "todo": "biking" },
          { "todo": "reading" }
      ],
      selectedTodoId: -1
    }
  },
  methods: {
    clearEditing() {
      this.selectedTodoId = -1;
    },
    addTodo() {
      this.todos.push({'todo': this.todo});
      this.todo = '';
    },
    remove(id) {
      this.todos.splice(id, 1);
    },
    toggleEdit(id) {
      this.selectedTodoId = id;
    },
    untoggleEdit() {
      this.selectedTodoId = -1;
    },
    isSelected(id) {
      return this.selectedTodoId == id;
    }
  }
}
// todo: add onload() => set focus on 'add todo' textbox
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .fa {
    float: right;
  }
  .fa:hover {
    cursor: pointer;
  }
  .fa-times-circle {
    position: relative;
    top: -35px;
  }
</style>
