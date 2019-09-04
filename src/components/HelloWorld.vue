<template>
  <div>
    <h1>components test</h1>
    <van-swipe :autoplay="3000" indicator-color="green">
      <van-swipe-item v-for="(image, index) in images" :key="index">
      <img :src="image" />
      </van-swipe-item>
    </van-swipe>
    <van-button type="primary">tianjiaxing</van-button>

        <!-- 优惠券单元格 -->
    <van-coupon-cell
      :coupons="coupons"
      :chosen-coupon="chosenCoupon"
      @click="showList = true"
    />

    <!-- 优惠券列表 -->
    <van-popup v-model="showList" position="bottom">
      <van-coupon-list
        :coupons="coupons"
        :chosen-coupon="chosenCoupon"
        :disabled-coupons="disabledCoupons"
        @change="onChange"
        @exchange="onExchange"
      />
    </van-popup>
  </div>
</template>

<script>
import Vue from 'vue'
import { Swipe, SwipeItem, Button, CouponCell, CouponList} from 'vant'
Vue.use(Swipe).use(SwipeItem).use(Button).use(CouponCell).use(CouponList)

const coupon = {
  available: 1,
  condition: '无使用门槛\n最多优惠12元',
  reason: '',
  value: 150,
  name: '优惠券名称',
  startAt: 1489104000,
  endAt: 1514592000,
  valueDesc: '1.5',
  unitDesc: '元'
};

export default {
  data() {
    return {
      images:[
        'https://img.yzcdn.cn/vant/apple-1.jpg',
        'https://img.yzcdn.cn/vant/apple-2.jpg'
      ],
      chosenCoupon: -1,
      coupons: [coupon],
      disabledCoupons: [coupon]
    }
  },

   methods: {
    onChange(index) {
      this.showList = false;
      this.chosenCoupon = index;
    },
    onExchange(code) {
      this.coupons.push(coupon);
    }
  }
 
}
</script>

<style lang="css" scoped>
  img {width:100%}
</style>