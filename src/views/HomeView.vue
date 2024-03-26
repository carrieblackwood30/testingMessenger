<template>
    <div>
        <ul v-for="user in  userArr " :key="user">
            <a href="/messenger">
                <li @click="chosenUser($event)" :data-value="user.name">{{ user.name }}</li>
            </a>
        </ul>
    </div>

</template>

<script setup>

import { userArr } from "../components/users.vue"

function chosenUser(event) {
    sessionStorage.setItem("chosenUser", event.target.getAttribute("data-value"))
}

</script>

<style scoped>
* {
    padding: 0;
    margin: 0;
    text-decoration: none;
    list-style: none;
    color: #f3f3f3;
}

div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background: rgba(255, 255, 255, .3);
    position: fixed;
    top: 0;
    right: 0;
    z-index: 10000;
    height: 100%;
    width: 100%;
}

li {
    border: 1px solid black;
    margin: 1rem;
    padding: 1rem;
    background: grey;
    border-radius: 10px;
    cursor: pointer;
}
</style>