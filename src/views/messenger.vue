<template>

    <body>
        <div class="chatContainer">

            <div class="users">
                <div class="user" v-for="user in userArr" :key="user">
                    <h3 :data-chosen="user.name" @click="chosenChat($event)">
                        {{ user.name }}
                    </h3>
                </div>
            </div>

            <div class="chat">
                <div class="messageContainer" v-for="chats in joshChat">
                    <h4>{{ chats.name }}</h4>
                    <p>{{ chats.message }}</p>
                </div>
                <div class="chatInput">
                    <input type="text" class="sendMessageInput" placeholder="Message" :value="sendingMessage"
                        @input="sendingMessage = $event.target.value">
                    <button class="sendMessageBtn" @click="sendMessage">></button>
                </div>
            </div>
        </div>
    </body>

</template>

<script setup>
import { reactive, ref } from "vue";

const emit = defineEmits(['change'])
const currentUser = sessionStorage.getItem("chosenUser")

import { userArr } from "../components/users.vue"

const sendingMessage = ref('')

import { joshChat } from "../components/joshChat.vue"


console.log(currentUser)

function chosenChat(event) {
    event.stopPropagation()
    console.log(event.target.getAttribute("data-chosen"))
}

function sendMessage(event) {
    event.stopPropagation()
    joshChat.push({
        name: `${currentUser}`,
        message: `${sendingMessage.value}`
    })

    localStorage.setItem(
        "messages",
        joshChat.push({
            name: `${currentUser}`,
            message: `${sendingMessage.value}`
        }))
}

console.log(joshChat)

</script>

<style scoped>
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    text-decoration: none;
}

:root {
    --main-color: #212121;
    --text-color: #f3f3f3;
}

body {
    background-color: #212121;
}

.userPick h1 {
    border: 1px solid black;
    margin: 1rem;
    padding: 1rem;
    background: var(--text-color);
    border-radius: 10px;
    cursor: pointer;
}

.userPick h1:hover {
    background-color: darkcyan;
}

.chatContainer {
    padding: 2rem;
    border: 1px solid black;
    display: flex;
    height: 100vh;
    width: 100%;
}

.chatContainer .users {
    display: flex;
    flex-direction: column;
    width: 40%;
    color: #f1f1f1;
    padding: 1rem;
    border: 1px solid black;
}

.chatContainer .users .user {
    border: 1px solid #f1f1f1;
    border-radius: 10px;
    width: 100%;
    padding: .5rem 1rem;
    margin: 1rem 0;
    padding: 1rem;
    font-size: 2rem;
}

.chat {
    background-image: url("https://blog.1a23.com/wp-content/uploads/sites/2/2020/02/Desktop.png");
    background-position: center;
    width: 100%;
    height: 100%;
    position: relative;
}

.chatInput {
    position: absolute;
    left: 0;
    bottom: 1%;
    right: 0;
    text-align: center;
}

.chatInput .sendMessageInput {
    width: 400px;
    padding: .8rem 1rem;
    border-radius: 10px;
    text-align: start;
    background-color: #212121;
    border: none;
    outline: none;
    color: #f3f3f3;
}

.chatInput .sendMessageBtn {
    background-color: #f3f3f3;
    border-radius: 50%;
    font-weight: 800;
    font-size: 1rem;
    padding: .4rem .8rem;
    cursor: pointer;
    border: none;
}

h3 {
    cursor: pointer;
    width: 100%;
    height: 100%;
}

.messageContainer {
    color: #f1f1f1;
    margin: 1rem;
    background: #212121;
    width: fit-content;
}

.messageContainer h4 {
    margin: .4rem 0;
    border-bottom: 1px solid;
    padding-bottom: .2rem;
}

.messageContainer p {
    font-size: 1.5rem;
    padding: .5rem 1rem;
}
</style>