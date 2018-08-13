<template>
    <div>
        <swiper>
            <swiper-slide>

            </swiper-slide>
        </swiper>
    </div>
</template>

<script>
    import 'swiper/dist/css/swiper/css'
    import {swiper, swiperSlide} from 'vue-awesome-swiper'

    export default {
        name: "swiperDefault",
        data() {
            return {
                slide: [1, 2, 3, 4, 5, 6]
            }
        },
        components: {swiperSlide, swiper},
    }
</script>

<style scoped>

</style>