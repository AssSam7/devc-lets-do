<template>
  <div>
    <add-to-do></add-to-do>
    <ul v-for="(todo, index) in todoActive" :key="index">
      <li>{{ todo.name }}</li>
    </ul>
  </div>
</template>

<script>
import AddToDo from "./Shared/AddToDo.vue";

export default {
  props: ["todoActive"],
  components: {
    addToDo: AddToDo
  }
};
</script>

<style lang="sass" scoped></style>
