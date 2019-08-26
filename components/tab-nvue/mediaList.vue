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
                            <view class="uni-list-cell">
                        <view class="uni-media-list">
                            <view class="uni-h5" style="display:flex;width: 100%;"> 8个评价 <text class="uni-h5" style="flex:2;padding-left:0px;">查看</text></view>
                            <view class="uni-media-list-text-bottom uni-ellipsis">业务范围:{{x.numName}}</view>
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
