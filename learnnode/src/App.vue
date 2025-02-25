<script setup>
import { computed, ref } from 'vue';
let id = 1;
let items = ref([
    { id: id++, name: 'Milk', isDone: true },
    { id: id++, name: 'Bread', isDone: false },
    { id: id++, name: 'Vodka', isDone: true },
    { id: id++, name: 'Beer', isDone: false },
    { id: id++, name: 'Chips', isDone: false },
]);
let newItem = ref('');

function add() {
    if (newItem.value.trim() !== '') {
        items.value.push({ id: id++, name: newItem.value, isDone: false });
    }
    newItem.value = '';
}

let doneItems = computed(() => items.value.filter(item => item.isDone));
let toDoItems = computed(() => items.value.filter(item => !item.isDone));
</script>
<template>
    <div class="container mt-3">
        <h1>All Items</h1>
        <ul>
            <li v-for="item in items" :key="item.id">
                    {{ item.name }}
                    <input type="checkbox" v-model="item.isDone">
                </li>
            </ul>

            <h1>Done Items</h1>
            <ul>
                <li v-for="item in doneItems" :key="item.id">
                    {{ item.name }}
                    <input type="checkbox" v-model="item.isDone">
                </li>
            </ul>

            <h1>ToDo Items</h1>
            <ul>
                <li v-for="item in toDoItems" :key="item.id">
                    {{ item.name }}
                    <input type="checkbox" v-model="item.isDone">
                </li>
            </ul>

        </div>
</template>,
<style></style>