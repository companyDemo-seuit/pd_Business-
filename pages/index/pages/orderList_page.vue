<template>
<view class="example ">

    <uni-nav-bar :fixed="false" color="#333333" background-color="#FFFFFF"  @click-left="showCity" @click-right="scan">
        <block slot="right">
            <view class="">
            </view>
        </block>
    </uni-nav-bar>
    <view class="" style="padding-top:20px;padding-bottom:40px;">
        <media-list :options="newsitem" @close="close(index1,index2)">
        </media-list>

    </view>
</view>
</template>
<script>
import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue'
import uniIcon from '@/components/uni-icon/uni-icon.vue'
import mediaList from '@/components/tab-nvue/orderList.vue';
export default {
    components: {
        uniNavBar,
        uniIcon,
        mediaList
    },
    data() {
        return {
            city: '北京',
            newsitem: [{
                "numName": '2号',
                "Invalid": false,
                "content": '等待处理',
                "datetime": "09-07 13:00",
                "clientName": '白女士',
                "phone": 15157364991,
                "adress": "万达三期1-301",
                "orderContent": '纱窗、阳台',
                "orderContentFee": 2000,
                "otherFee": 20,
                "totleFee": 2020,
            }, {
                "numName": '1号',
                "Invalid": true,
                "content": '订单已无效',
                "datetime": "09-07 13:00",
                "clientName": '白女士',
                "phone": 15157364991,
                "adress": "万达三期1-301",
                "orderContent": '纱窗、阳台',
                "orderContentFee": 2000,
                "otherFee": 20,
                "totleFee": 2020,

            }, ]
        }
    },
    onLoad(e) {
        this.title = e.title || '';
        this.test_get()
    },
    methods: {
        goDetail(e) {
            uni.navigateTo({
                url: '/pages/tabBar/dashboard/orderDetail/orderDetail?title=' + e.title
            });
        },
        showCity() {
            uni.showToast({
                title: '选择城市'
            });
        },
        scan() {
            uni.showToast({
                title: '扫码'
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
                    // this.city = res
                    console.log(res);
                });
        },
        test_post() {
            // 基本同GET
            this.$request({
                    url: '/admin/get_product_list'
                }, 'POST')
                .then(res => {
                    console.log(res);
                });
        }

    }
}
</script>
<style>
/* page {
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
    background:linear-gradient(top,rgb(49, 147, 186,1) 1%,rgb(117, 216, 250) 99%);
    background-size:100%
} */

/* 搜索框 */

.city {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    width: 100%;
    margin-left: 8px;
    white-space: nowrap;
}

.input-view {
    width: 92%;
    display: flex;
    background-color: #e7e7e7;
    height: 30px;
    border-radius: 15px;
    padding: 0 4%;
    flex-wrap: nowrap;
    margin: 7px 0;
    line-height: 30px;
}

.input-view .uni-icon {
    line-height: 30px !important;
}

.input-view .input {
    height: 30px;
    line-height: 30px;
    width: 94%;
    padding: 0 3%;
}

/* 搜索框 */
</style>
