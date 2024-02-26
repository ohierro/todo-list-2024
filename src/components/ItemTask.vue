<script setup lang="ts">

const emits = defineEmits(['toggleCompleted', 'deleteTask'])

const props = defineProps<{
    id: number
    name: string,
    completed: boolean,
}>()
</script>

<template>
<v-row align="center">
    <v-col cols="2">
        <v-checkbox :model-value="completed" @click="emits('toggleCompleted', id)"></v-checkbox>
    </v-col>
    <v-col cols="8">
        <span :class="{ done: completed }">
            {{ name }}
        </span>
    </v-col>
    <v-col cols="2">
        <v-btn 
            @click="emits('deleteTask', id)"    
            icon="mdi-delete"
        ></v-btn>
    </v-col>
</v-row>  
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>