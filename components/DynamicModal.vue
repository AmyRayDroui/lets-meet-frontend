<template>
    <div v-if="modalSettings.isOpen" class="dynamic-modal-backdrop"
        @click.stop="modalSettings = { isOpen: false, component: '' }"></div>
    <div v-if="modalSettings.isOpen">
        <div class="dynamic-modal" @click="">
            <component :is="modalSettings.component"></component>
        </div>
    </div>
</template>

<script setup lang="ts">
const emits = defineEmits()
const { $bus }: any = useNuxtApp()

const modalSettings = shallowRef({
    isOpen: false,
    component: ''
})

//Modal global event listeners
$bus.$on('signUp', (e: any) => { setModal(e) })
const setModal = (settings: any) => {//TODO: change to modalSettings interface
    console.log('setting modal')
    modalSettings.value = settings
}


</script>