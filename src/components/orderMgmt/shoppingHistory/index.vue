<template>
    <div class="shoppingHistory-container">
        <tab active-color="#64C0F4" defaultColor="#333" bar-active-color="#64C0F4">
            <tab-item :selected="index == 0" @on-item-click="onItemClick(0)">全部</tab-item>
            <tab-item :selected="index == 1" @on-item-click="onItemClick(1)">待审核</tab-item>
            <tab-item :selected="index == 2" @on-item-click="onItemClick(2)">待收款</tab-item>
            <tab-item :selected="index == 3" @on-item-click="onItemClick(3)">已收款</tab-item>
            <tab-item :selected="index == 4" @on-item-click="onItemClick(4)">待发货</tab-item>
        </tab>
        <swiper v-model="index" :show-dots="false" @on-index-change="itemChange">
            <swiper-item v-for="(item,index) in itemList" :key="index">
                <shopping-item></shopping-item>
            </swiper-item>
        </swiper>
    </div>
</template>
<script>
    import {Tab, TabItem, Swiper, SwiperItem} from 'vux';
    import shoppingItem from './sub/shoppingItem.vue';
    export default {
        components: {
            Tab,
            TabItem,
            Swiper,
            SwiperItem,
            shoppingItem
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
                        path: '/shoppingItem0'
                    },
                    {
                        name: '待审核',
                        path: '/shoppingItem1'
                    },
                    {
                        name: '待付款',
                        path: '/shoppingItem2'
                    },
                    {
                        name: '待收货',
                        path: '/shoppingItem3'
                    },
                    {
                        name: '已入库',
                        path: '/shoppingItem4'
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
    .shoppingHistory-container{
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