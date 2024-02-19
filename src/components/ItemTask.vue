<script setup lang="ts">

const emits = defineEmits(['add'])
const props = defineProps<{
    id: number
    name: string,
    completed: boolean,
}>()

function onClick() {

}
</script>

<template>
<v-row align="center">
    <v-col cols="2">
        <v-checkbox></v-checkbox>
    </v-col>
    <v-col cols="8">
        <span :class="{ done: completed }">
            {{ name }}
        </span>
    </v-col>
    <v-col cols="2">
        <v-btn 
            @click="onClick"    
            icon="mdi-delete"
        ></v-btn>
    </v-col>
</v-row>  
</template>