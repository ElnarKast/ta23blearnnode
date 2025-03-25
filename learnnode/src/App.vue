<script setup>
import { ref } from 'vue';
import RouterTabs from './components/RouterTabs.vue';
</script>
<template>
    <Suspense>
        <RouterView></RouterView>
    </Suspense>
    <div class="container" v-if="$route.meta.container === undefined">
        <section class="section">
            <RouterView></RouterView>
        </section>
    </div>
    <Suspense v-else>
         <RouterView></RouterView>
    </Suspense>
</template>