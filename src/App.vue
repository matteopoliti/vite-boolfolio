<script>

import { store } from "./store";
import HeaderApp from './components/Header/HeaderApp.vue'


export default {
    components: {
        HeaderApp,
        
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
    
    <router-view></router-view>
</template>

<style lang="scss">
@use "./styles/general.scss";
</style>