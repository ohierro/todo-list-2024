<script setup lang="ts">

const props = defineProps(['todos'])

function onClick(id: number) {
    console.log(`click on task ${id}`);
}
</script>

<template>
    <v-card v-for="todo in todos">
        <v-row align="center">
            <v-col cols="2">
                <v-checkbox></v-checkbox>
            </v-col>
            <v-col cols="8">
                <span :class="{ done: todo.completed }">
                    {{ todo.name }}
                </span>
            </v-col>
            <v-col cols="2">
                <v-btn 
                    @click="onClick(todo.id)"    
                    icon="mdi-delete"
                ></v-btn>
            </v-col>
        </v-row>    
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