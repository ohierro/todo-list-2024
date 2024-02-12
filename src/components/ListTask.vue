<script setup lang="ts">

const props = defineProps(['todos'])

function onClick(id: number) {
    console.log(`click on task ${id}`);
}
</script>

<template>
    <div v-for="todo in todos">
        <input type="checkbox" name="" id=""> 
        {{ todo.name }}
        <button @click="onClick(todo.id)">X</button>
    </div>
</template>