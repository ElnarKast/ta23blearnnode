<script setup>
import { ref } from 'vue';

let items = ref(['Milk', 'Bread', 'Vodka', 'Beer', 'Chips']);
let newItem = ref('');

function add(){
    if(newItem.value.trim() !== ''){
    items.value.push(newItem.value)
    }
    newItem.value="";
}

</script>
<template>
    <div class="container mt-3">
        <div class="content">
            <div class="fields has-addons">
                <div class="controll is-expanded">
                    <input class="input" type = "text" v-model="newItem" @keypress.enter = "add">
                </div>
                <div class="control">
                    <button class="button is-primary" @click="add">Add</button>
                </div>
            </div>    

            <ul>
                <li v-for="item in items">{{ item }}</li>
            </ul>
        </div>
    </div>
</template>,
<style></style>