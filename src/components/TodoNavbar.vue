<template>
<div class="navbar bg-base-100">
  <div class="flex-1">
    <a class="btn btn-ghost text-xl">Todo-pinia</a>
  </div>
  <div class="navbar-end">
    <button class="btn btn-ghost btn-circle" @click="toggleMenu">
      <div class="indicator relative">
        <div v-show="showMenu">
          <ul class="menu menu-horizontal bg-base-200 rounded-box w-80 absolute top-0 right-3 overflow-y-scroll min-h-[200px] max-h-[200px] z-[10]">
            <li v-if="todoList.length" v-for="todo in todoList.slice().reverse()" :key="todo.id" class="w-full">
              <div class="flex flex-col items-start">
                <p class="text-primary">{{ todo.item }}</p>
                <small>
                  Created at 
                  {{`${todo.createdAt.toLocaleDateString()} - ${todo.createdAt.toLocaleTimeString()}`}}
                </small>
              </div>
            </li>
            <li v-else>
              <div>
                No notifications available
              </div>
            </li>
          </ul>
        </div>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor">
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
        </svg>
        <span class="badge badge-xs badge-primary indicator-item">{{ todoList.length }}</span>
      </div>
    </button>
    <div class="dropdown dropdown-end">
      <div tabindex="0" role="button" class="btn btn-ghost btn-circle avatar">
        <div class="w-10 rounded-full">
          <img
            alt="Tailwind CSS Navbar component"
            src="../assets/logo-pinia.png" />
        </div>
      </div>
    </div>
  </div>
</div>
</template>
  
<script>
import { ref } from 'vue';
import { storeToRefs } from 'pinia'
import { useTodoListStore } from '@/store/useTodoListStore'
export default {
  setup() {
    const store = useTodoListStore()
    const { todoList } = storeToRefs(store)
    let showMenu = ref(false)

    const toggleMenu = () => {
      showMenu.value = !showMenu.value
    }

    return { todoList, showMenu, toggleMenu }
  }
}
</script>

<style>

</style>