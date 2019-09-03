<template>
  <div>
    <van-swipe :autoplay="3000" indicator-color="white">
      <van-swipe-item>tian</van-swipe-item>
      <van-swipe-item>jia</van-swipe-item>
      <van-swipe-item>xing</van-swipe-item>
    </van-swipe>
  </div>
</template>

<script>
import Vue from 'vue'
import { Swipe, SwipeItem } from 'vant'
Vue.use(Swipe).use(SwipeItem)
export default {
  // components: {
  //   Button, 
  //   Swipe, 
  //   SwipeItem
  // }
 
}
</script>