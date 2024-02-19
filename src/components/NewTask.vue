<script setup lang="ts">
import { computed, ref } from 'vue';


const emits = defineEmits(['add'])
const name = ref('')

function onAdd() {
    emits('add', name.value)
    name.value = ''
}

const enableButton = computed( () => {
    return name.value.length > 0
})
</script>

<template>
    <v-row align="center">
        <v-col cols="10">
            <v-text-field 
                label="Label"
                v-model="name"
            >
            </v-text-field>
        </v-col>
        <v-col>
            <v-btn 
                @click="onAdd" 
                prepend-icon="mdi-plus"
                :disabled="!enableButton"
            >
                add
            </v-btn>
        </v-col>
    </v-row>
</template>