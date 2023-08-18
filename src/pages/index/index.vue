<script setup lang="ts">
import CustomNavbar from '@/pages/index/componets/CustomNavbar.vue'
import { getHomeBannerAPI, getHomeCategoryAPI } from '@/services/home'
import { onLoad } from '@dcloudio/uni-app'
import { ref } from 'vue'
import type { BannerItem, CategoryItem } from '@/types/home'
import CategoryPanel from '@/pages/index/componets/CategoryPanel.vue'
import HotPanel from '@/pages/index/componets/HotPanel.vue'

const bannerList = ref<BannerItem[]>([])

// 获取轮播图数据
const getHomeBannerData = async () => {
  const res = await getHomeBannerAPI()
  bannerList.value = res.result
}

// 获取前台分类数据
const CategoryList = ref<CategoryItem[]>([])
const getHomeCategoryData = async () => {
  const res = await getHomeCategoryAPI()
  CategoryList.value = res.result
}

onLoad(() => {
  getHomeBannerData()
  getHomeCategoryData()
})
</script>

<template>
  <!-- 自定义导航栏 -->
  <CustomNavbar />

  <!-- 自定义轮播图 -->
  <XtxSwiper :list="bannerList" />

  <!-- 分类面板 -->
  <CategoryPanel :list="CategoryList" />

  <!-- 热门推荐 -->
  <HotPanel />

  <view class="index">index</view>
</template>

<style lang="scss">
//
page {
  background-color: #f7f7f7;
}
</style>
