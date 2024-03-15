<script setup lang="ts">
import { reactive } from 'vue';
import Header from './components/Header.vue'
import NewTask from '@/components/NewTask.vue'
import ListTask from '@/components/ListTask.vue'
import CounterTask from '@/components/CounterTask.vue'
import { isTemplateSpan } from 'typescript';
import ItemTask from './components/ItemTask.vue';

interface Task {
  id: number,
  name: string,
  completed: boolean
}

const todos = reactive<Array<Task>>([
  {
    id: 0,
    name: 'Create the best TODO application in the world',
    completed: true
  },
  {
    id: 1,
    name: 'Publish in github pages',
    completed: false
  }
])

function addTodo(name: string) {
  todos.push({
    id: todos.length,
    name: name,
    completed: false
  })
}

function onToggleCompleted(id: number) {
  const item = todos.filter(t => t.id === id)[0]
  item.completed = !item.completed
}

function onDeleteTask(id: number) {
  const index = todos.findIndex(t => t.id === id)
  todos.splice(index, 1)
}

</script>

<template>
  <header>
    <Header></Header>
  </header>

  <main>
    <NewTask @add="addTodo"></NewTask>
    <ListTask :todos="todos"
      @toggle-completed="onToggleCompleted"
      @delete-task="onDeleteTask"
    ></ListTask>
    <CounterTask :items="todos"></CounterTask>
  </main>

  <footer>
    Esto es el footer
  </footer>
</template>

<style scoped>
header {
  line-height: 1.5;
  font-size: 35px;
  text-align: center;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

main {
  flex-grow: 2;
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
