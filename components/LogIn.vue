<template>
    <form @submit.prevent="">
        <label for="email">Email</label>
        <input type="email" id="email">
        <label for="password">password</label>
        <input type="password" id="password">
        <button type="submit">Log in</button>
        <small>not a member yet? <button @click="toSignup" class="button-as-link">Sign up</button></small>
    </form>
</template>

<script setup lang="ts">
const { $bus }: any = useNuxtApp()
const toSignup = () => {
    $bus.$emit('signUp', { isOpen: true, component: 'SignUp' })
}
</script>