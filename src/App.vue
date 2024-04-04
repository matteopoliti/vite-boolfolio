<script>

import { store } from "./store";
import MainApp from './Main/MainApp.vue'

export default {
    components: {
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
    <MainApp />
</template>

<style lang="scss">
@use "./styles/general.scss";
</style>