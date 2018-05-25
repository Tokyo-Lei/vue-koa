<template>
    <div>
        <van-row class="test-row">
            <van-col span="4">span:4</van-col>
            <van-col span="16">span:8</van-col>
            <van-col span="4">span:4</van-col>
        </van-row>
    </div>
</template>

<script>
    export default {
        name: "ShoppingMail",
        data(){
            return{
                msg: 'stone'
            }
        }
    }
</script>

<style scoped>
    .test-row{
        text-align: center;
    }
</style>