<template>
    <div v-if="modalSettings.isOpen" class="dynamic-modal-backdrop"
        @click.stop="modalSettings = { isOpen: false, component: '' }"></div>
    <div v-if="modalSettings.isOpen && dynamicComponent">
        <div class="dynamic-modal" @click="">
            <component :is="dynamicComponent? dynamicComponent : ''"></component>
        </div>
    </div>
</template>

<script setup lang="ts">
import { render } from 'vue';
import { ref } from 'vue';
const { $bus }: any = useNuxtApp()

const modalSettings = shallowRef({
    isOpen: false,
    component: 'SignUp'
})
let dynamicComponent: any
const cmpSignUp = resolveComponent('SignUp')
const cmpLogIn = resolveComponent('LogIn')

watch(modalSettings, (newVal) => {
    switch (newVal.component) {
        case 'SignUp':
            dynamicComponent = cmpSignUp
            break;
        case 'LogIn':
            dynamicComponent = cmpLogIn
            break;
        default:
            dynamicComponent = cmpLogIn
            break;
    }
})

//Modal global event listeners
$bus.$on('signUp', (e: any) => { setModal(e) })
$bus.$on('logIn', (e: any) => { setModal(e) })
const setModal = (settings: any) => {//TODO: change to modalSettings interface
    modalSettings.value = settings
}


</script>