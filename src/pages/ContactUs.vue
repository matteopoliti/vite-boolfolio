<template>
    <div class="container">
        <h1>Contact Us</h1>
        <ContactForm></ContactForm>
    </div>
</template>

<script>
import ContactForm from '../components/ContactForm.vue'

export default {
    name: 'ContactUs',
    components: {
        ContactForm
    },
    data () {
        

        return {

        }
    },
    methods: {
        
    },
    mounted() {
        
    },
}
</script>

<style lang="scss" scoped>
h1{
    margin-bottom: 20px;
    text-align: center;
}
</style>