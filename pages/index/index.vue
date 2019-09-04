<template>
<view class="content swbg">
    <choosepage v-if="page_code=='choose'"></choosepage>
    <orderList v-if="page_code=='order'"></orderList>
    <shopList v-if="page_code=='shop'"></shopList>
    <pageTwo v-if="page_code=='publish'"></pageTwo>
    <pageThree v-if="page_code=='my'"></pageThree>

    <footerNav></footerNav>

    <uni-popup :show=type position="middle" mode="fixed" @hidePopup="togglePopup(false)">
        <button type="primary" @click="ChooseType('1')">业主版</button>
        <button type="primary" @click="ChooseType('2')">商家版</button>
    </uni-popup>
</view>
</template>

<script>
import choosepage from "./pages/choose_page.vue";
import orderList from "./pages/orderList_page.vue";
import shopList from "./pages/shopList_page.vue";
import pageTwo from "./pages/page_two.vue";
import pageThree from "./pages/page_three.vue";
import footerNav from "../../components/footer/footer_nav.vue";
import uniPopup from '@/components/uni-popup/uni-popup.vue'
export default {
    data() {
        return {
            type: false,
        }
    },
    components: {
        choosepage,
        orderList,
        shopList,
        pageTwo,
        pageThree,
        footerNav,
        uniPopup
    },

    computed: {
        page_code() {
            let page_code
            if (this.$store.state.footer_store.footer_nav[this.$store.state.footer_store.now_page_index]) {
                page_code = this.$store.state.footer_store.footer_nav[this.$store.state.footer_store.now_page_index].name_code
            } else {
                page_code = 'choose'
            }
            return page_code
        }
    },
    onLoad() {
        this.type = true
        console.log('index onload')
    },
    methods: {
        open_loading() {
            this.$loading()
        },
        togglePopup(type) {
            this.type = type
        },
        ChooseType(type) {
            this.type = false
            if (type == '1') {
                this.$store.dispatch('menu_3')
                this.$store.commit("change_page", 0)
		            uni.setNavigationBarTitle({
		                title: this.hasSetText = "商家列表"
		            })
            } else {
                this.$store.dispatch('menu_4')
                this.$store.commit("change_page", 0)
		            uni.setNavigationBarTitle({
		                title: this.hasSetText = "待处理"
		            })
            }
        }
    }

}
</script>

<style>
.content {
    padding-bottom: 400upx;
}

.logo {
    height: 200upx;
    width: 200upx;
    margin-top: 200upx;
}

.title {
    font-size: 36upx;
    color: #8f8f94;
}
</style>
