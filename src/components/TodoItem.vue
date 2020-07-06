<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed" />
      <strong>{{index + 1 }}</strong>
      {{todo.title | uppercase}}
    </span>
    <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    }
  }
};
</script>

<style scoped>
li {
  border: 1px solid;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 1rem;
  margin-bottom: 1rem;
}

.rm {
  background: #a0cb8a;
  color: #fff;
  border-radius: 50%;
  font-weight: bold;
  border: none;
}
input {
  margin-right: 1rem;
}

.done {
  text-decoration: line-through;
}
</style>