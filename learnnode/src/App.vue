<script setup>
import { ref } from 'vue';
import RouterTabs from './components/RouterTabs.vue';
</script>
<template>
    <Suspense>
        <RouterView></RouterView>
    </Suspense>
    <div class="container">
        <section class="section">
            <RouterView></RouterView>
        </section>
    </div>
</template>