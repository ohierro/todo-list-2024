<script setup lang="ts">
import ItemTask from './ItemTask.vue';


const props = defineProps(['todos'])

function onClick(id: number) {
    console.log(`click on task ${id}`);
}
</script>

<template>
    <v-card v-for="todo in todos">
        <item-task 
            :id="todo.id"
            :name="todo.name"
            :completed="todo.completed"
        ></item-task>
    </v-card>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}

.v-card {
    margin-top: 10px;
}
</style>