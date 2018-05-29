<template>
    <div>
        <div class="search-bar">
            <van-row>
                <van-col span="3">
                    <img :src="locationIcon" width="80%" class="location-icon">
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
        <!--swiper area-->
        <div class="swiper-area">
            <van-swipe :autoplay="1000">   <!--vant的swiper组件， 绑定轮播时间间隔-->
                <van-swipe-item v-for="(banner, index) in bannerPicArr" :key="index">
                    <img v-lazy="banner.imageUrl" width="100%" alt="">  <!--绑定图片懒加载-->
                </van-swipe-item>
            </van-swipe>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: "ShoppingMail",
        data() {
            return {
                msg: 'stone',
                locationIcon: require('../../assets/images/location.png'),
                bannerPicArr: [
                    {imageUrl: 'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic001.jpg'},
                    {imageUrl: 'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic002.jpg'},
                    {imageUrl: 'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic003.jpg'},
                ]
            }
        },
        created(){
            axios({
                url: 'https://www.easy-mock.com/mock/5b0cc25d60480528d24b9bcc/vue-koa/index',  /* easy-mock创建的首页接口地址*/
                method: 'get'
            }).then(res => {
                console.log(res);
            }).catch(err => {
                console.log(err);
            })
        }
    }
</script>

<style scoped>
    .search-bar {
        height: 2.2rem;
        background-color: #e5017d;
        line-height: 2.2rem;
        overflow: hidden;
    }

    .search-input {
        width: 100%;
        height: 1.3rem;
        border-top: 0;
        border-left: 0;
        border-right: 0;
        border-bottom: 1px solid #FFF !important; /*!important;优先使用设置的样式，不要默认值*/
        background-color: #e5017d;
        color: #FFFFFF;
    }

    .location-icon {
        padding-top: 0.2rem;
        padding-left: 0.2rem;
    }

    .swiper-area {
        clear: both;
        max-height: 15rem; /*因为van-swipe轮播组件刚开始时不能计算出图片的高度。会导致三个点在下面。这是最大高度，并隐藏即可*/
        overflow: hidden;
    }
</style>