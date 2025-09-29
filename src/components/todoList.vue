<script setup lang="ts">
import { ref, computed   } from 'vue'



const todos = ref([
    { text: 'Learn Vue 3', done: true },
    { text: 'Learn React', done: false },
    { text: 'Learn Docker', done: false }
])

const remaining = computed(() => {
    return todos.value.filter(todo => !todo.done).length
})
</script>

<template>
    <div>
        <h1>Todo List</h1>
        <ul>
            <li v-for="(todo,i) in todos" :key="i">
                <input type="checkbox" v-model="todo.done" />
                <span :style="{ textDecoration: todo.done ? 'line-through' : 'none' }">{{ todo.text }}</span>

            </li>
        </ul>
    </div>
</template>