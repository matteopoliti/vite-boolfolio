<template>
    <div>
        <h2>Contact Form</h2>

        <div>
            <form @submit.prevent="sendForm()">
                <div>
                    <input type="text" name="name" placeholder="inserisci il tuo nome" v-model="name">
                </div>
                <p v-for="(error, index) in errors.name" :key="`message-errors-${index}`"> 
                    {{ error }}
                </p>

                <div>
                    <input type="email" name="email" placeholder="inserisci la tua email" v-model="email">
                </div>
                <p v-for="(error, index) in errors.email" :key="`message-errors-${index}`"> 
                    {{ error }}
                </p>

                <div>
                    <textarea name="message" id="message" cols="30" rows="10" v-model="message"></textarea>
                </div>
                <p v-for="(error, index) in errors.message" :key="`message-errors-${index}`"> 
                    {{ error }}
                </p>

                <button type="submit">Send</button>
            </form>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'ContactForm',
    data () {
        return {
            name: '',
            email: '',
            message: '',
            errors: {},
            success: false
        }
    },
    methods: {
        sendForm(){
            const data = {
                name: this.name,
                email: this.email,
                message: this.message
            }

            this.errors = {};

            axios.post( 'http://127.0.0.1:8000/api/contacts', data)
                .then( res=>{

                    this.success = res.data.success;

                    if(!this.success){
                        this.errors = res.data.errors
                    }else{
                        this.name = '',
                        this.email = '',
                        this.message = ''
                    }
                })
        }
    },
    mounted() {
        
    },
}
</script>

<style lang="scss" scoped>

</style>