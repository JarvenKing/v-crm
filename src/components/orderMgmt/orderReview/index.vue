<template>
    <div class="orderReview-container">
        <tab active-color="#64C0F4" defaultColor="#333" bar-active-color="#64C0F4">
            <tab-item :selected="index == 0" @on-item-click="onItemClick(0)">全部</tab-item>
            <tab-item :selected="index == 1" @on-item-click="onItemClick(1)">订单审核</tab-item>
            <tab-item :selected="index == 2" @on-item-click="onItemClick(2)">定制审核</tab-item>
            <tab-item :selected="index == 3" @on-item-click="onItemClick(3)">退货审核</tab-item>
        </tab>
        <swiper v-model="index" :show-dots="false" @on-index-change="itemChange">
            <swiper-item v-for="(item,index) in itemList" :key="index">
                <review-item></review-item>
            </swiper-item>
        </swiper>
    </div>
</template>
<script>
    import {Tab, TabItem, Swiper, SwiperItem} from 'vux';
    import reviewItem from './sub/reviewItem.vue';
    export default {
        components: {
            Tab,
            TabItem,
            Swiper,
            SwiperItem,
            reviewItem
        },
        mounted () {
            this.setTitle();
            this.itemList.forEach((el,i) => {
                if(this.$route.path == el.path){
                    //this.index = i;
                    this.itemChange(i);
                }
            });
        },
        data () {
            return {
                index: 0,
                itemList: [
                    {
                        name: '全部',
                        path: '/reviewItem0'
                    },
                    {
                        name: '订单审核',
                        path: '/reviewItem1'
                    },
                    {
                        name: '定制审核',
                        path: '/reviewItem2'
                    },
                    {
                        name: '退货审核',
                        path: '/reviewItem3'
                    }
                ]
            }
        },
        watch: {
            '$route' (to, from) {
                this.itemList.forEach( (el,i) => {
                    if(el.path == to.path){
                        this.index = i;
                    }
                });
            }
        },
        methods: {
            onItemClick(i) {
                this.index = i;
                this.$router.replace(this.itemList[i].path);
            },
            itemChange(i) {
                this.index = i;
                this.$router.replace(this.itemList[i].path);
            }
        }
    }
</script>
<style lang="less">
    .orderReview-container{
        background-color: #f5f5f5;
    .vux-slider{
        height: calc(~ '100% - 44px');
    }
    .vux-swiper{
        height: 100% !important;
    }
    .vux-swiper-item{
        overflow: scroll;
    }
    }
</style>