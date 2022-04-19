<template>
  <div id="app">
    <TodoHeader />
    <TodoInput v-on:addTodo="addTodo" />
    <TodoList :todoItems="todoItems" @removeTodo="removeTodo"/>
    <TodoFooter @removeAll="clearAll"/>
  </div>
</template>

<script>
import TodoFooter from "./components/TodoFooter.vue";
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "app",
  data() {
    return {
      todoItems: [],
    };
  },
  created() {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  components: {
    TodoFooter: TodoFooter,
    TodoHeader: TodoHeader,
    TodoInput: TodoInput,
    TodoList: TodoList,
  },
  methods: {
    addTodo(todoItems){
      localStorage.setItem(todoItems, todoItems);
      this.todoItems.push(todoItems);
    },
    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    },
    removeTodo(a, i){
      localStorage.removeItem(a);
      this.todoItems.splice(i, 1);
    }
  },
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

body {
  text-align: center;
  background-color: #f6f6f8;
}

input {
  border-style: groove;
  width: 200px;
}

button {
  border-style: groove;
}

.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>
