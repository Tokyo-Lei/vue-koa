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
            <van-swipe :autoplay="3000">   <!--vant的swiper组件， 绑定轮播时间间隔-->
                <van-swipe-item v-for="(banner, index) in bannerPicArr" :key="index">
                    <img v-lazy="banner.image" width="100%" alt="">  <!--绑定图片懒加载-->
                </van-swipe-item>
            </van-swipe>
        </div>
        <!-- type bar 导航 -->
        <div class="type-bar">
            <div v-for="(cate,index) in category" :key="index">
                <img v-lazy="cate.image" width="90%"/>
                <span>{{cate.mallCategoryName}}</span>
            </div>
        </div>

        <!-- adBanner area -->
        <div>
            <img v-lazy="adBanner" width="100%" alt="">
        </div>
        <!--Recommend goods area-->
        <div class="recommend-area">
            <div class="recommend-title">
                商品推荐
            </div>
            <div class="recommend-body">
                <swiper>
                    <swiper-slide>
                        <div class="recommend-item">
                            <img src="" width="80%" alt="">
                            <div>

                            </div>
                            <div>
            
                            </div>
                        </div>
                    </swiper-slide>
                </swiper>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'
    import 'swiper/dist/css/swiper.css'
    import {swiper, swiperSlide} from 'vue-awesome-swiper'

    export default {
        name: "ShoppingMail",
        data() {
            return {
                locationIcon: require('../../assets/images/location.png'),//定位图
                bannerPicArr: [],//轮播图数据
                category: [],//导航数据
                adBanner: '',//广告
                recommendGoods: [],//推荐商品

            }
        },
        components: {swiper, swiperSlide},//推荐区域轮播组件
        created() {
            axios({
                url: 'https://www.easy-mock.com/mock/5b0cc25d60480528d24b9bcc/vue-koa/index', /* easy-mock创建的首页接口地址*/
                method: 'get'
            }).then(res => {
                console.log(res);
                if (res.status == 200) {
                    this.category = res.data.data.category;//导航图
                    this.adBanner = res.data.data.advertesPicture.PICTURE_ADDRESS;//广告图
                    this.bannerPicArr = res.data.data.slides;//轮播图
                    this.recommendGoods = res.data.data.recommend;//推荐商品
                }
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
        max-height: 10rem; /*因为van-swipe轮播组件刚开始时不能计算出图片的高度。会导致三个点在下面。这是最大高度，并隐藏即可*/
        overflow: hidden;
    }

    .type-bar {
        background-color: #fff;
        margin: 0 .3rem .3rem .3rem;
        border-radius: .3rem;
        font-size: 14px;
        display: flex;
        flex-direction: row;
        flex-wrap: nowrap;
    }

    .type-bar div {
        padding: .3rem;
        font-size: 12px;
        text-align: center;
        flex: 1;
    }

    .recommend-area {
        background-color: #ffffff;
        margin-top: 0.3rem;
    }

    .recommend-title {
        border-bottom: 1px solid #eee;
        padding: 0.2rem;
        font-size: 14px;
        color: #e5017d
    }
</style>