<template>
    <div>
        <ul v-for="user in userArr" :key="user">
        <li><button @click="chosenUser($event)">{{ user.name }}</button></li>
    </ul>
    </div>

</template>

<script setup>
    import { ref } from "vue";

    const userArr = ref([{
        id: 1,
        name: "Josh"
    },
    {
        id:2,
        name:"Ann",
    },
    {
        "id":3,
        "name": "Sam"
    }
    ])

   function chosenUser(event){
        console.log(event.currentTarget.name);
    }

</script>

<style scoped>
    *{
        text-decoration: none;
        list-style: none;
        color: #f3f3f3;
    }

    div{
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background: rgba(255,255,255,.3);
        position: fixed;
        top: 0; right: 0;
        z-index: 10000;
        height: 100%; 
        width: 100%;
    }

    li button{
        border: 1px solid black;
        margin: 1rem;
        padding: 1rem;
        background: grey;
        border-radius: 10px;
        cursor: pointer;
    }
</style>