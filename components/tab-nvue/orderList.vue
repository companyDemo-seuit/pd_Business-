<template>
<view>
    <view class="list-cell " style="padding:0px 20px  0px  20px;">
        <view v-for="x in options">
            <view class="media-list" v-if="x.numName" @click="bindClick">

                <view v-show="!x.Invalid" style="display: flex;">
                    <view class="uni-list" style="flex: 6;">
                        <view class="uni-list-cell">
                            <view class="uni-media-list">
                                <view class="uni-media-list-logo">
                                    <view class="uni-media-list-text-top">{{x.numName}}</view>
                                </view>
                                <view class="uni-media-list-body">
                                    <view class="uni-media-list-text-top">{{x.content}}</view>
                                    <view class="uni-text" style="display:flex;width: 100%;">
                                        下单时间： <text class="uni-h5" style="flex:2;padding-left:0px;">{{x.datetime}}</text></view>
                                </view>
                            </view>
                        </view>
                        <view class="uni-msg-list">
                            <view class="button-sp-area uni-h5" style="padding: 10px 0 0 0;">
                                <view class="uni-h5" style="display:flex;width: 100%;"> {{x.clientName}} {{x.phone}}</view>
                            </view>
                        </view>
                        <view class="uni-msg-list">
                            <view class="button-sp-area uni-h5" style="padding: 10px 0 0 0;">
                                <view class="uni-media-list-text-bottom uni-ellipsis" style="width: 130%;">地址:{{x.adress}}</view>
                            </view>
                        </view>
                        <view class="uni-msg-list">
                            <view class="button-sp-area uni-h5" style="padding: 10px 0 0 0;">
                                <view class="uni-h5" style="display:flex;width: 100%;">{{x.orderContent}}：<text class="uni-h5" style="flex:2;padding-left:0px;">{{x.orderContentFee}}</text></view>
                            </view>
                        </view>
                        <view class="uni-msg-list">
                            <view class="button-sp-area uni-h5" style="padding: 10px 0 0 0;">
                                <view class="uni-h5" style="display:flex;width: 100%;"> 其他：<text class="uni-h5" style="flex:2;padding-left:0px;">{{x.otherFee}}</text></view>
                            </view>
                        </view>
                        <view class="uni-msg-list">
                            <view class="button-sp-area uni-h5" style="padding: 10px 0 0 0;">
                                <view class="uni-h5" style="display:flex;width: 100%;"> 总计：<text class="uni-h5" style="flex:2;padding-left:0px;">{{x.totleFee}}</text></view>
                            </view>
                        </view>
                        <view class="uni-msg-list">
                            <view class="button-sp-area uni-h5" style="padding: 10px 0 0 0;">
                                <button class="mini-btn" type="default" size="mini">取消</button>
                                <button class="mini-btn" type="primary" size="mini" style="margin-left:10px;" hover-class="uni-list-cell-hover" @click="goDetail">开始处理</button>
                            </view>
                        </view>
                    </view>
                </view>

                <view v-show="x.Invalid" style="display: flex;">
                    <view class="uni-list" style="flex: 6;">
                        <view class="uni-list-cell">
                            <view class="uni-media-list">
                                <view class="uni-media-list-logo">
                                    <view class="uni-media-list-text-top">{{x.numName}}</view>
                                </view>
                                <view class="uni-media-list-body">
                                    <view class="uni-media-list-text-top">{{x.content}}</view>
                                    <view class="uni-text" style="display:flex;width: 100%;">
                                        下单时间： <text class="uni-h5" style="flex:2;padding-left:0px;">{{x.datetime}}</text></view>

                                </view>
                            </view>
                        </view>
                    </view>
                </view>



            </view>
        </view>
    </view>
</view>
</template>

<script>
import uniRate from '@/components/uni-rate/uni-rate.vue'
export default {
    components: {
        uniRate
    },
    props: {
        options: {
            type: Object,
            default: function(e) {
                return {}
            }
        }
    },
    methods: {
        close(e) {
            this.$emit('close');
        },
        bindClick() {
            this.$emit('click');
        }
    }
}
</script>

<style>
.title {
    padding: 20upx;
}
</style>
