<script>
import TodoForm from '@/components/TodoForm.vue';
import TodoList from '@/components/TodoList.vue';
import TodoNavbar from '@/components/TodoNavbar.vue';

export default {
  components: { TodoForm, TodoList, TodoNavbar },
  setup() {

  }
}
</script>

<template>
  <TodoNavbar />
  <main>
    <TodoForm />
    <TodoList />
  </main>
</template>

<style scoped>
main {
  /* display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center; */
}
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
