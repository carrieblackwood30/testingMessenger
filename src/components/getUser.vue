<template>
    <ul v-for="user in userArr" :key="user">
        <li><a href="/messenger">{{ user }}</a></li>
    </ul>
</template>

<script setup>
    import { ref } from "vue";

    const userArr = ref(['Josh', 'Ann', 'Sam'])
</script>

<style scoped>
    *{
        text-decoration: none;
        list-style: none;
    }
</style>