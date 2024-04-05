<script>

import { store } from "./store";
import HeaderApp from './components/Header/HeaderApp.vue'
import MainApp from './components/Main/MainApp.vue'

export default {
    components: {
        HeaderApp,
        MainApp
    },
    data() {
        return {
            store,
        };
    },
    created() {
    },
}
</script>

<template>
    <HeaderApp />
    <MainApp />
</template>

<style lang="scss">
@use "./styles/general.scss";
</style>