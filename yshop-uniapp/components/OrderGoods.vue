<template>
  <view class="orderGoods">
    <view class="total">共{{ cartInfo.length }}件商品</view>
    <view class="goodWrapper">
      <view class="item acea-row row-between-wrapper" v-for="cart in cartInfo" :key="cart.id">
        <view class="pictrue">
          <image :src="cart.productInfo.image" class="image" />
        </view>
        <view class="text">
          <view class="acea-row row-between-wrapper">
            <view class="name line1">{{ cart.productInfo.storeName }}</view>
            <view class="num">x {{ cart.cartNum }}</view>
          </view>
          <view
            class="attr line1"
            v-if="cart.productInfo.attrInfo"
          >{{ cart.productInfo.attrInfo.suk }}</view>
          <view class="money font-color-red">￥{{ cart.truePrice }}</view>
          <view class="evaluate" v-if="evaluate == 3" @click="routerGo(cart)">评价</view>
        </view>
      </view>
    </view>
  </view>
</template>
<script>
export default {
  name: "OrderGoods",
  props: {
    evaluate: Number,
    cartInfo: {
      type: Array,
      default: () => []
    }
  },
  data: function() {
    return {};
  },
  mounted: function() {},
  methods: {
    routerGo(cart) {
      this.$yrouter.push({
        path: "/pages/shop/GoodsEvaluate/index",
        query: { id: cart.unique }
      });
    }
  }
};
</script>
