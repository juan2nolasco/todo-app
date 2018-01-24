<template>
<div>
    <p class="tasks">Completed Task: {{ todos.filter(todo => {return todo.done == true}).length}}</p>
    <p class="tasks">Pending Task: {{todos.filter(todo => {return todo.done == false}).lenght}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" v-bind:todo="todo" ></todo>
</div>
</template>0
<script>
import Todo from './Todo';
export default {
  props: ['todos'],
  components: {
      Todo,
  },
  methods: {
      deleteTodo(todo) {
          const todoIndex = this.todos.indexOf(todo);
          this.todos.splice(todoIndex, 1);
      },
      completeTodo(todo) {
          const todoIndex = this.todos.indexOf(todo);
          this.todos[todoIndex].done = true;
      },
  }
}
</script>

<style scoped>
p.tasks {
    text-align: center;
}
</style>


