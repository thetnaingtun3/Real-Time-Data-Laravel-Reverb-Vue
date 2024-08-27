<script setup>
import { ref } from "vue";

const messages = ref([]);
// const count = ref(0);
// Echo.channel("messages").listen("HelloWorld", (e) => {
//     console.log(e);
//     count.value++;
// });
const message = ref("");
function handleSubmit() {
    messages.value.push({
        id: crypto.randomUUID(),
        // id: messages.value.length + 1,
        message: message.value,
    });
    message.value = "";
}
</script>

<template>
    <ul>
        <li v-for="message in messages" :key="message.id">
            {{ message.message }}
        </li>
    </ul>
    <form @submit.prevent="handleSubmit">
        <input v-model="message"></input>
        <button>Send Message</button>
    </form>
</template>
