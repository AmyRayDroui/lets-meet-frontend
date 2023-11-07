<template>
  <div>
    <h2>Welcome to let's meet</h2>
    <h3>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Dignissimos libero harum suscipit voluptatum fugiat quia
      sed esse facere doloremque eaque?</h3>
    <button @click="signUp">Sign Up</button>
  </div>
</template>

<script setup lang="ts">
const { $bus }: any = useNuxtApp()
import { onMounted } from 'vue'
//Components
const SignUp = resolveComponent('SignUp')

onMounted(() => { signUp() })

const signUp = () => {
  $bus.$emit('signUp', { isOpen: true, component: SignUp })
}
</script>
