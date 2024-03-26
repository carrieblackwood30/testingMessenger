<template>
    <body>
        <div class="chatContainer">
        <div class="users">
            <div class="user" v-for="user in userArr" :key="user">
                <h3>
                    {{ user }}
                </h3>
            </div>
        </div>
        <div class="chat">
            <div class="chatInput">
                <input type="text" class="sendMessageInput" placeholder="Message">
                <button class="sendMessageBtn">></button>
            </div>
        </div>
    </div>
    </body>
</template>

<script setup>
    import { ref } from "vue";

    const userArr = ref(['Josh', 'Ann', 'Sam'])

</script>

<style scoped>
*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    text-decoration: none;
}

:root{
    --main-color: #212121;
    --text-color: #f3f3f3;
}

body{
    background-color: #212121;
}

.userPick h1{
    border: 1px solid black;
    margin: 1rem;
    padding: 1rem;
    background: var(--text-color);
    border-radius: 10px;
    cursor: pointer;
}

.userPick h1:hover{
    background-color: darkcyan;
}

.chatContainer{
    padding: 2rem;
    border: 1px solid black;
    display: flex;
    height: 100vh;
    width: 100%;
}

.chatContainer .users{
    display: flex;
    flex-direction: column;
    width: 40%;
    color: #f1f1f1;
    padding: 1rem;
    border: 1px solid black;
}

.chatContainer .users .user{
    border: 1px solid #f1f1f1;
    border-radius: 10px;
    width: 100%;
    padding: .5rem 1rem;
}

.chat{
    background-image: url("https://blog.1a23.com/wp-content/uploads/sites/2/2020/02/Desktop.png");
    background-position: center;
    width: 100%;
    height: 100%;
    position: relative;
}

.chatInput{
    position: absolute;
    left: 0;
    bottom: 1%;
    right: 0;
    text-align: center;
}

.chatInput .sendMessageInput{
    width: 400px;
    padding: .8rem 1rem;
    border-radius: 10px;
    text-align: start;
    background-color: #212121;
    border: none;
    outline: none;
    color: #f3f3f3;
}

.chatInput .sendMessageBtn{
    background-color: #f3f3f3;
    border-radius: 50%;
    font-weight: 800;
    font-size: 1rem;
    padding: .4rem .8rem;
    cursor: pointer;
    border: none;
}

h3{
    margin: 1rem;
    cursor: pointer;
}
</style>