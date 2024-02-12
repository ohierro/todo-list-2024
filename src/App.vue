<script setup lang="ts">
import { reactive } from 'vue';
import Header from './components/Header.vue'
import NewTask from '@/components/NewTask.vue'
import ListTask from '@/components/ListTask.vue'
import CounterTask from '@/components/CounterTask.vue'

const todos = reactive([
  {
    id: 0,
    name: 'Create the best TODO application in the world',
    completed: false
  }, 
  {
    id: 1,
    name: 'Publish in github pages',
    completed: false
  }
])
</script>

<template>
  <header>
    <Header></Header>
  </header>

  <main>
    <NewTask></NewTask>
    <ListTask :todos="todos"></ListTask>
    <CounterTask></CounterTask>
  </main>
</template>

<style scoped>
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
