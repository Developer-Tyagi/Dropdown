<template>
    <div>
        <h1>{{ greeting }}</h1>
    </div>
</template>

<script>
import { computed } from 'vue';

export default {
    setup() {

        const greeting = computed(() => {
            return `Hello from VUE`;
        });

        return {
            greeting,
        };
    },
};
</script>
