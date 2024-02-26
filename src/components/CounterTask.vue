<script setup lang="ts">
import { computed } from 'vue';

interface Task {
    id: number
    name: string,
    completed: boolean,
}

const props = defineProps<{
    items: Array<Task>
}>()

const completedTasks = computed(() => props.items.filter(i => i.completed).length)
const totalTasks = computed(() => props.items.length)
</script>

<template>
<div>
    {{ completedTasks }} of {{  totalTasks }} completed
</div>
</template>