<template>
    <div>
        <div class="">
            <label for="Email">Email</label>
            <input v-model="email" type="text">
        </div>
        <div class="">
            <label for="Password">Password</label>
            <input v-model="password" type="password">
        </div>
        <button :disabled="!(email.length > 0 && password.length > 0)">Login</button>
    </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeMount } from 'vue';
import type { Ref } from 'vue';

const email: Ref<string> = ref('')
const password: Ref<string> = ref('') 

onBeforeMount(() => {
    console.log("antes de crear")
})

onMounted(() => {
    console.log("Montado")
})

</script>

<style scoped>

</style>