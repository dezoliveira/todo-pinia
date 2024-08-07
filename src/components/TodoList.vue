<template>
  <div v-for="todo in todoList" :key="todo.id">
    <span :class="{ completed: todo.completed }">{{ todo.item }}</span>
    <span
      @click.stop="toggleCompleted(todo.id)"
    >
      &#10004
    </span>
  </div>
</template>

<script>
import { useTodoListStore } from '@/store/useTodoListStore';
import { storeToRefs } from 'pinia';

export default {
  setup() {
    const store = useTodoListStore()
    const { todoList } = storeToRefs(store)
    const { toggleCompleted } = store

    return {
      todoList,
      toggleCompleted
    }
  }
}
</script>

<style>
.completed {
  text-decoration: line-through;
}
</style>