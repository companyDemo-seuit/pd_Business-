<template>
<view style="padding-bottom: 500upx;">

  <view class="des">选择页面未跳转</view>
</view>
</template>
<script>
export default {
  data() {
    return {};
  },
  computed: {
    list() {
      return this.$store.state.list;
    }
  },
  methods: {
    open_loading() {
      this.$loading();
    },
    get_detail(id) {
      uni.navigateTo({
        url: '/pages/detail/detail?id=' + id
      });
    },
    test_get() {
      this.$request({
          url: '/admin/get_product_list',
          data: {
            a: 1
          }
        }, 'GET')
        .then(res => {
          this.$alert('状态码：' + res.code);
          console.log(res);
        });
    },
    test_post() {
      // 基本同GET
      this.$request({
				url: '/admin/get_product_list'
			}, 'POST')
        .then(res => {
          this.$alert(res.code);
          console.log(res);
        });
    }
  }
};
</script>

<style>
.item {
  font-size: 28upx;
  line-height: 60upx;
  height: 60upx;
  border-bottom: 2upx solid #f1f1f1;
  padding-left: 30upx;
  padding-right: 30upx;
  color: #888;
  text-align: left;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.des {
  text-align: center;
  padding: 30upx;
  margin-top: 100upx;
  font-size: 30upx;
  color: #888888;
}

button {
  width: 330upx;
  float: left;
  margin-left: 30upx;
  margin-top: 30upx;
  padding: 10upx 20upx;
  font-size: 32upx;
}
</style>
