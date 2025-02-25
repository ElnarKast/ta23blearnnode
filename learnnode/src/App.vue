<script setup>
import { computed, ref } from 'vue';
import ItemList from './ItemList.vue';
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
        <ItemList :items="items" title="All Items"></ItemList>
        <ItemList :items="doneItems" title="Done Items"></ItemList>
        <ItemList :items="toDoItems" title="Todo Items"></ItemList>

    </div>
</template>,
<style></style>