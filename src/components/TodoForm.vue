<template>
  <form @submit.prevent="addItemAndClear(todo)">
    <div class="flex gap-2 p-4">
      <input v-model="todo" type="text" class="input input-bordered w-full max-w-xs"/>
      <button class="btn btn-primary">Add</button>
    </div>
  </form>
</template>

<script>
import { ref } from 'vue';

import { useTodoListStore } from '@/store/useTodoListStore';
export default {
  setup() {
    const todo = ref("")
    const store = useTodoListStore()

    const addItemAndClear = (item) => {
      if (item.length === 0) {
        return
      }

      store.addTodo(item)
      todo.value = ''
    }

    return {
      todo,
      addItemAndClear
    }
  }
}
</script>

<style>

</style>