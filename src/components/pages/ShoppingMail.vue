<template>
    <div>
        <div class="search-bar">
            <van-row>
                <van-col span="3">
                    <img :src="licationIcon" width="80%" class="location-icon">
                </van-col>
                <van-col span="16">
                    <input type="text" class="search-input">
                </van-col>
                <van-col span="5" class="">
                    <van-button size="mini">
                        查找
                    </van-button>
                </van-col>
            </van-row>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ShoppingMail",
        data() {
            return {
                msg: 'stone',
                licationIcon: require('../../assets/images/location.png')
            }
        }
    }
</script>

<style scoped>
    .search-bar{
        height: 2.2rem;
        background-color: #e5017d;
        line-height: 2.2rem;
    }

    .search-input{
        width: 100%;
        height: 1.3rem;
        border-top: 0;
        border-left: 0;
        border-right: 0;
        border-bottom: 1px solid #FFF !important;  /*!important;优先使用设置的样式，不要默认值*/
        background-color: #e5017d;
        color: #FFFFFF;
    }

    .location-icon{qq
        padding-top: 0.2rem;
        padding-left: 0.2rem;
    }
</style>