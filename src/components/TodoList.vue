<template>
  <ul v-show="todoList.length" class="menu bg-base-200 rounded-box">
    <li v-for="todo in todoList" :key="todo.id">
      <div :class="{ completed: todo.completed }">
        <span>{{ todo.item }}</span>
        <div class="flex justify-end">
          <span v-if="todo.completed">
            <h5 class="text-sm">
              <span class="badge badge-success mx-2">Done</span>
            </h5>
          </span>
          <span v-else>
            <h5 class="text-sm">
              <span class="badge badge-primary mx-2">Open</span>
            </h5>
          </span>
          <span
            @click.stop="toggleCompleted(todo.id)"
          >
            &#10004
          </span>
          <span @click="deleteTodo(todo.id)">&#10060</span>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
import { useTodoListStore } from '@/store/useTodoListStore';
import { storeToRefs } from 'pinia';

export default {
  setup() {
    const store = useTodoListStore()
    const { todoList } = storeToRefs(store)
    const { toggleCompleted, deleteTodo } = store

    return {
      todoList,
      toggleCompleted,
      deleteTodo
    }
  }
}
</script>

<style>
.completed {
  text-decoration: line-through;
  opacity: 0.4;
}
</style>