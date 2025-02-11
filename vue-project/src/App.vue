<template>
  <div>
    <AddForm @addTodo="addTodo" />
    <TodoList 
      :todos="todos" 
      @changeTodos="changeTodos" 
      @deleteTodoByid="deleteTodoByid" 
    />
  </div>
</template>

<script>
import AddForm from './components/AddForm.vue';
import TodoList from './components/TodoList.vue';

export default {
  components: {
    AddForm,
    TodoList,
  },
  data() {
    return {
      todos: [
        { id: 1, title: 'Помыть руки', completed: true },
        { id: 2, title: 'Сделать зарядку', completed: false },
        { id: 3, title: 'Наконец изучить React', completed: true },
      ],
    };
  },
  methods: {
    addTodo(title) {
      const trimmedTitle = title.trim();
      if (!trimmedTitle) {
        console.warn('Пустая задача не может быть добавлена.');
        return;
      }
      const newTodo = {
        id: Date.now(),
        title: trimmedTitle,
        completed: false,
      };
      this.todos.push(newTodo);
      console.log('Добавлена новая задача:', newTodo);
    },
    deleteTodoByid(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
      console.log('Задача с ID удалена:', id);
    },
    changeTodos(id) {
      const todo = this.todos.find(todo => todo.id === id);
      if (todo) {
        todo.completed = !todo.completed;
        console.log('Изменено состояние задачи:', todo);
      }
    }
  }
};
</script>

