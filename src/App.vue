<template>
  <div class="container">
    <header class="header">
      <h1>#todo</h1>

      <main class="header__content">
        <div class="buttons">
          <div class="all">
            <button class="btn btn__all" @click="currentToDo = 'All'">
              All
            </button>
            <hr v-if="currentToDo === 'All'" />
          </div>
          <div class="active">
            <button class="btn btn__active" @click="currentToDo = 'Active'">
              Active
            </button>
            <hr v-if="currentToDo === 'Active'" />
          </div>
          <div class="completed">
            <button
              class="btn btn__completed"
              @click="currentToDo = 'Completed'"
            >
              Completed
            </button>
            <hr v-if="currentToDo === 'Completed'" />
          </div>
        </div>
      </main>
    </header>

    <div class="todo__content">
      <div class="todo__all" v-if="currentToDo === 'All'">
        <app-todo-all
          :todoList="todoList"
          @completeTodo="completeTodo($event)"
          @unCompleteTodo="unCompleteTodo($event)"
        ></app-todo-all>
      </div>
      <div class="todo__active" v-if="currentToDo === 'Active'">
        <app-todo-active :todoActive="todoActive"></app-todo-active>
      </div>
      <div class="todo__completed" v-if="currentToDo === 'Completed'"></div>
    </div>
  </div>
</template>

<script>
import TodoAll from "./components/TodoAll.vue";
import TodoActive from "./components/TodoActive.vue";

export default {
  name: "app",
  data() {
    return {
      currentToDo: "All",
      todoList: [
        { name: "First Todo", completed: false },
        { name: "Second Todo", completed: false },
        { name: "Third Todo", completed: true }
      ]
    };
  },
  methods: {
    completeTodo(index) {
      console.log("Completed " + index);
      this.todoList[index].completed = true;
    },
    unCompleteTodo(index) {
      console.log("Pending " + index);
      this.todoList[index].completed = false;
    }
  },
  components: {
    appTodoAll: TodoAll,
    appTodoActive: TodoActive
  },
  computed: {
    todoActive: function() {
      return this.todoList.filter(todo => todo.completed);
    }
  }
};
</script>

<style lang="scss" scoped>
h1 {
  font-family: "Raleway", sans-serif;
  font-style: normal;
  font-size: 3rem;
  font-weight: 700;
  color: #333333;
  text-align: center;
}

main {
  max-width: 70%;
  padding: 6rem 0;
  padding-bottom: 0;
  margin: auto;
}

.todo__content {
  max-width: 70%;
  margin: 2rem auto;
}

.buttons {
  border-bottom: 1px solid #bdbdbd;

  display: flex;
  justify-content: space-around;
}

.btn {
  cursor: pointer;
  color: #333333;
  border: 0;
  outline: none;
  background: none;
  padding: 1rem 2rem;
  padding-bottom: 1.5rem;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Montserrat;
  font-style: normal;
  font-weight: 600;
  font-size: 1.4rem;
}

.all,
.active,
.completed {
  hr {
    height: 2px;
    color: transparent;
    background: #2f80ed;
    border-radius: 4px 4px 0px 0px;
  }
}
</style>
