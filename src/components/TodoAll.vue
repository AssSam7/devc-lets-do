<template>
  <div>
    <add-to-do> </add-to-do>
    <div class="list">
      <label
        v-for="(todo, index) in todoList"
        :key="index"
        class="checkbox item"
      >
        <input
          type="checkbox"
          :data-index="index"
          :checked="todo.completed"
          v-model="todo.completed"
          @click="processTodo($event, index)"
        />
        <span :class="{ strike: todo.completed }">{{ todo.name }}</span>
      </label>
    </div>
  </div>
</template>

<script>
import AddToDo from "./Shared/AddToDo.vue";

export default {
  props: ["todoList"],
  data() {
    return {};
  },
  methods: {
    processTodo(e, index) {
      if (e.target.checked) {
        // console.log("Checked!", index);
        this.$emit("completeTodo", index);
      } else {
        // console.log("Unchecked!", index);
        this.$emit("unCompleteTodo", index);
      }
    }
  },
  computed: {},
  components: {
    addToDo: AddToDo
  }
};
</script>

<style lang="scss" scoped>
// Strike through line
.strike {
  text-decoration-line: line-through;
}

.list {
  margin: 2rem 0;
}

.item {
  width: 100%;
  margin-top: 2rem;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.checkbox {
  display: flex;
  cursor: pointer;
  position: relative;
}

.checkbox > span {
  font-family: Montserrat;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  color: #222;
}

.checkbox > input {
  margin-right: 1rem;
  height: 20px;
  width: 20px;
  -webkit-appearance: none;
  -moz-appearance: none;
  -o-appearance: none;
  appearance: none;
  border: 1px solid #828282;
  box-sizing: border-box;
  border-radius: 4px;
  outline: none;
  transition-duration: 0.3s;
  cursor: pointer;
}

.checkbox > input:checked {
  border: 1px solid #41b883;
  background: #2f80ed;
}

.checkbox > input:checked + span::before {
  content: "\2713";
  font-size: 1.7rem;
  display: block;
  text-align: center;
  color: #fff;
  position: absolute;
  left: 0.4rem;
}

.checkbox > input:active {
  border: 2px solid #34495e;
}
</style>
