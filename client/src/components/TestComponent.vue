<script setup lang="ts">
const props = defineProps<{username: string; age: number}>();
const ages = props.age + 1;
</script>

<template>
    <h1>This is test component.</h1>
    User: {{ props.username }}
    <br>
    Age: {{  ages }}

    <slot></slot>
    <p><slot name="description"></slot></p>
</template>

<style scoped>
    h1 {
        color: yellow;
    }
    p {
        color: green;
    }
</style>