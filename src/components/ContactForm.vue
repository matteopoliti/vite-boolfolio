<template>
    <div class="form">

        <div class="alert" v-if="success">
            Messaggio inviato correttamenete
        </div>
        
        <form @submit.prevent="sendForm()">
            <div>
                <input type="text" name="name" placeholder="inserisci il tuo nome" v-model="name">
            </div>
            <p v-for="(error, index) in errors?.name" :key="`message-errors-${index}`"> 
                {{ error }}
            </p>

            <div>
                <input type="email" name="email" placeholder="inserisci la tua email" v-model="email">
            </div>
            <p v-for="(error, index) in errors?.email" :key="`message-errors-${index}`"> 
                {{ error }}
            </p>

            <div>
                <textarea name="message" id="message" cols="30" rows="10" v-model="message"></textarea>
            </div>
            <p v-for="(error, index) in errors?.message" :key="`message-errors-${index}`"> 
                {{ error }}
            </p>

            <button type="submit">Send</button>
        </form>
    
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

.form {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    
    .alert{
        background-color: #d1e7dd;
        border: 1px solid #a3cfbb;
        color: #0a3622;
        padding: 16px;
        border-radius: 6px;
        margin-bottom: 16px;
    }
    input,
    textarea {
        width: 100%;
        padding: 16px;
        margin-bottom: 15px;
        border: 1px solid #ccc;
        border-radius: 3px;
        font-size: 20px;
    }
    
    
    p {
        color: red;
        font-size: 14px;
        margin-bottom: 5px;
    }
    
    
    button {
        background-color: #007bff;
        color: #fff;
        font-size: 20px;
        border: none;
        padding: 10px 40px;
        border-radius: 3px;
        cursor: pointer;
        &:hover {
            background-color: #0056b3;
        }
    }
    
}

</style>