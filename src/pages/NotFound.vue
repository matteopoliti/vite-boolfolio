<template>
    <div class="error">
        <div class="text">
            <h1>Page Not Found</h1>
            <p>We can't seem to find the page you're looking for. Please check the URL for any typos.</p>

        </div>
        <div>
            <img src="https://th.bing.com/th/id/OIG2.Wihvt7irWKA0pvo5fd7z?w=1024&h=1024&rs=1&pid=ImgDetMain" alt="">
        </div>
    </div>
</template>

<script>
export default {
    name: 'NotFound',
    data () {
        

        return {}
    }
}
</script>

<style lang="scss" scoped>
.error{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    column-gap: 20px;
    .text{
        width: 450px;
        h1{
            font-size: 35px;
            margin-bottom: 15px;
        }
        p{
            font-size: 20px;
            margin-bottom: 15px;
        }
    }
    img{
        width: 420px
    }
}
</style>