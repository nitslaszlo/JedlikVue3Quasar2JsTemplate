<template>
  <div>
    <p>{{ title }}</p>
    <ul>
      <li v-for="todo in todos" :key="todo.id" @click="increment">
        {{ todo.id }} - {{ todo.content }}
      </li>
    </ul>
    <p>Count: {{ todoCount }} / {{ meta.totalCount }}</p>
    <p>Active: {{ active ? 'yes' : 'no' }}</p>
    <p>Clicks on todos: {{ clickCount }}</p>
  </div>
</template>

<script>
import { defineComponent, computed, ref, toRef } from 'vue';

function useClickCount() {
  const clickCount = ref(0);

  function increment() {
    clickCount.value += 1;
    return clickCount.value;
  }
  return { clickCount, increment };
}

function useDisplayTodo(todos) {
  const todoCount = computed(() => todos.value.length);
  return { todoCount };
}

export default defineComponent({
  name: 'ExampleComponent',
  props: {
    title: {
      type: String,
      required: true
    },
    todos: {
      type: Array,
      default: () => []
    },
    meta: {
      type: Object,
      required: true
    },
    active: {
      type: Boolean
    }
  },
  setup(props) {
    return { ...useClickCount(), ...useDisplayTodo(toRef(props, 'todos')) };
  }
});
</script>
