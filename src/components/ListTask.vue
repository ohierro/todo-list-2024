<script setup lang="ts">
import ItemTask from './ItemTask.vue';


const emits = defineEmits(['toggleCompleted', 'deleteTask'])
const props = defineProps(['todos'])

function onClick(id: number) {
    console.log(`click on task ${id}`);
}

function toggleCompleted(id: number) {
    emits('toggleCompleted', id)
}

function onDeleteTask(id: number) {
    emits('deleteTask', id)
}

</script>

<template>
    <!-- <v-card v-for="todo in todos"> -->
        <item-task
            v-for="todo in todos"   
            :id="todo.id"
            :name="todo.name"
            :completed="todo.completed"
            @toggle-completed="toggleCompleted"
            @delete-task="onDeleteTask"
        ></item-task>
    <!-- </v-card> -->
</template>

<style scoped>
.done {
    text-decoration: line-through;
}

.v-card {
    margin-top: 10px;
}
</style>