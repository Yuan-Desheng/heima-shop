<script setup lang="ts">
import CustomNavbar from '@/pages/index/componets/CustomNavbar.vue'
import XtxSwiper from '@/components/XtxSwiper.vue'
import { getHomeBannerAPI } from '@/services/home'
import { onLoad } from '@dcloudio/uni-app'

const getHomeBannerData = async () => {
  const res = await getHomeBannerAPI()
  console.log(res, 'res')
}

onLoad(() => {
  getHomeBannerData()
})
</script>

<template>
  <custom-navbar></custom-navbar>

  <xtx-swiper></xtx-swiper>

  <view class="index">index</view>
</template>

<style lang="scss">
//
</style>
