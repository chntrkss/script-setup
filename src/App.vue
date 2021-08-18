<template>
    <div class="container mt-5">
        <div v-if="showChild" ref="myAlert" class="alert alert-success mb-5">
            Component
        </div>
        <button class="btn btn-primary" @click="showChild = !showChild">
            Toggle
        </button>
    </div>
</template>

<script lang="ts" setup>
    import { onBeforeMount, onMounted, onUpdated, ref } from "vue";

    const showChild = ref(true)
    const myAlert = ref<(HTMLHeadingElement | HTMLElement)>(null)

    onBeforeMount(() => {
        console.log("onBeforeMount")
        console.log("onBeforeMount=>", myAlert.value)
    })

    onMounted(() => {
        console.log("onMounted")
        console.log("onMounted=>", myAlert.value)

        if (myAlert.value) {
            myAlert.value.style.fontSize = 40 + "px"
        }

    })

    onUpdated(() => {
        console.log("Dom update edildi")
        if (myAlert.value instanceof HTMLElement) {
            myAlert.value.style.color = "red"
        }
    }) 
</script>

<style lang="scss">
    @import url("https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css");
    @import url("https://fonts.googleapis.com/icon?family=Material+Icons");
</style>
