<template>
  <div>
    <todo-header v-bind:additem="addItem"></todo-header>
    <todo-input v-on:add="addTodoItem"></todo-input>
    <todo-list v-bind:todolist="todoItems" v-on:delete="deleteTodoItem"></todo-list>
    <todo-footer v-on:remove="removeTodoItem"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  components: {
    'todo-header': TodoHeader,
    'todo-input': TodoInput,
    'todo-list': TodoList,
    'todo-footer': TodoFooter,
  },
  data() {
    return {
      todoItems: [],
      addItem: '',
    }
  },
  methods: {
    fetchTodoItems: function() {
      for(var i=0; i<localStorage.length; i++) {
          var item = localStorage.key(i);
          this.todoItems.push(item);
      }
    },
    addTodoItem: function(value) {
      this.todoItems.push(value);
      localStorage.setItem(value, value);
      this.addItem = value;
    },
    removeTodoItem: function() {
      this.todoItems = [];
      localStorage.clear();
    },
    deleteTodoItem: function(todo, index) {
      this.todoItems.splice(index,1); //화면에서만 안보이도록 함
      localStorage.removeItem(todo);
    }
  },
  created: function() {
    // 페이지가 생성되고 컴포넌트가 호출될 떄 실행되는 로직
    this.fetchTodoItems();
  },
}
</script>

<style>

</style>
