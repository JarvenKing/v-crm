<template>
    <div class="reviewInfo-container">
        <div class="reviewInfo-list">
            <div class="address">
                <div class="address-name">
                    <div>
                        <span>收货人</span><span>:</span>
                    </div>
                    <div>
                        <span>收货地址</span><span>:</span>
                    </div>
                </div>
                <div class="address-info">
                    <div>
                        <span>ALTABA集团科技公司</span>
                        <span style="color:#fff;background-color: #64C0F4;width: 60px;text-align: center;line-height: 2.0em;">沟通</span>
                    </div>
                    <div>
                        <span>北京朝阳区奥运街道鸟巢运动场,北京朝阳区奥运街道鸟巢运动场,北京朝阳区奥运街道鸟巢运动场</span>
                    </div>
                </div>
            </div>
            <div class="reviewInfo-container-h">
                <span>当当塑料制品有限公司</span>
                <span>2017-05-13</span>
            </div>
            <div class="reviewInfo-container-c">
                <div class="reviewInfo-l">
                    <img src="../../../../assets/img/stock-item.png" alt="">
                </div>
                <div class="reviewInfo-m">
                    <span>A类1型号商品</span>
                    <span>高级定制版黑色塑料置物架</span>
                    <span style="color: #666;">采购说明：请准时交货,并保证商品质量</span>
                    <span style="color: #666;">发货时间：2017-04-01前</span>
                </div>
                <div class="reviewInfo-r">
                    <span style="color: #ed0737">￥5000</span>
                    <span style="color: #64C0F4;">X100件</span>
                </div>
            </div>
            <div class="reviewInfo-container-c">
                <div class="reviewInfo-l">
                    <img src="../../../../assets/img/stock-item.png" alt="">
                </div>

                <div class="reviewInfo-m">
                    <span>A类1型号商品</span>
                    <span>高级定制版黑色塑料置物架</span>
                    <span style="color: #666;">采购说明：请准时交货,并保证商品质量</span>
                    <span style="color: #666;">发货时间：2017-04-01前</span>
                </div>
                <div class="reviewInfo-r">
                    <span style="color: #ed0737">￥5000</span>
                    <span style="color: #64C0F4;">X100件</span>
                </div>
            </div>
            <div style="font-size: 12px;background-color: #f5f5f5;padding: 5px 0 5px 10px;margin-top: 10px;">
                <span>订单说明：加双蛋，少盐</span>
            </div>
            <div class="reviewInfo-container-b">
                <div class="reviewInfo-container-b-l">
                    <div>
                        <div>
                            <span>采购员：</span><span style="color: #666;">张三</span>
                        </div>
                        <div>
                            <span>电话：</span><span style="color: #666;">15654321234</span>
                        </div>
                    </div>
                </div>
                <div class="reviewInfo-container-b-r">
                    <div>
                        <span>合计</span><span style="font-size: 14px;color: #ed0737;">￥10000</span>
                    </div>
                </div>
            </div>
            <div class="reviewInfo-group">
                <div style="flex-basis: 70px;flex-grow: 0;flex-shrink: 0;height: 43px;line-height: 43px;padding-left: 10px;">
                    <span>审核结果：</span>
                </div>
                <div style="flex-shrink: 1;flex-grow: 1;">
                    <checklist required label-position="left" :options="reviewSelect" v-model="reviewResult" @on-change="change"></checklist>
                </div>
            </div>
            <div class="reviewInfo-group">
                <div style="flex-basis: 70px;flex-grow: 0;flex-shrink: 0;height: 43px;line-height: 43px;padding-left: 10px;">
                    <span>审核意见：</span>
                </div>
                <div style="flex-shrink: 1;flex-grow: 1;">
                    <input type="text" placeholder="请填写审核意见（20字以内）">
                </div>
            </div>
            <div class="reviewInfo-group" @click="dafaultShow = true">
                <div style="flex-basis: 70px;flex-grow: 0;flex-shrink: 0;height: 43px;line-height: 43px;padding-left: 10px;">
                    <span>审批历史：</span>
                </div>
                <div style="flex-shrink: 1;flex-grow: 1;height: 43px;">
                    <i class="right"></i>
                </div>
                <div v-transfer-dom>
                    <popup v-model="dafaultShow" position="right" width="100%">
                        <div class="review-popup">
                            <div class="clearfloat" style="background-color: #fff;border-bottom: 1px solid #ccc;">
                                <i class="left" @click="dafaultShow = false"></i>
                            </div>
                            <div class="popup-content">
                                <span class="popup-item1">驳回订单</span>
                                <span class="popup-item2">修改商品A数量为15</span>
                                <span class="popup-item3">2017-04-17</span>
                            </div>
                        </div>
                    </popup>
                </div>
            </div>
        </div>
        <footer>
            <span>确定</span>
        </footer>
    </div>
</template>
<script>
    import { TransferDom,Checklist,Popup } from 'vux';
    export default {
        directives: {
            TransferDom
        },
        components: {
            Checklist,
            Popup
        },
        data(){
            return {
                dafaultShow: false,
                reviewSelect: [
                    {key: 'resolve',value: '接受订单'},{key: 'reject',value: '驳回订单'}
                ],
                reviewResult: ['resolve']
            }
        },
        methods: {
            change(val){
                this.$nextTick(function(){
                    this.reviewResult = [val[this.reviewResult.length - 1]];

                })
            }
        }
    }
</script>
<style lang="less">
    .review-popup{
        .vux-close{
            width: 24px;
            height: 24px;
            text-align: center;
            border-radius: 11px;
            background-color: #fff;
            border: 1px solid #98979d;
        }
        .left{
            display: block;
            width: 22px;
            height: 22px;
            background-image: url('../../../../assets/img/left.png');
            background-size: cover;
            float: left;
            margin-top: 10px;
            margin-bottom: 10px;
        }
        .popup-content{
            display: flex;
            justify-content: space-between;
            line-height: 2.5em;
            background-color: #fff;
            font-size: 14px;
            border-bottom: 1px solid #ccc;
        }
            .popup-item1{
                flex-basis: 64px;
                flex-grow: 0;
                flex-shrink: 0;
                margin-left: 10px;
            }
            .popup-item2{
                flex-grow: 1;
                flex-shrink: 1;
                text-align: center;
            }
            .popup-item3{
                flex-basis: 89px;
                flex-grow: 0;
                flex-shrink: 0;
                margin-right: 10px;
            }
    }
    .reviewInfo-container{
        background-color: #f5f5f5;
        .reviewInfo-list{
            background-color: #fff;
            margin-bottom: 45px;
            .address{
                font-size: 14px;
                color: #666;
                display: flex;
                padding-top: 10px;
                border-bottom: 1px solid #ccc;
                padding-bottom: 10px;
                .address-name{
                    flex-basis: 60px;
                    flex-shrink: 0;
                    margin-left: 10px;
                    div{
                        display: flex;
                        justify-content: space-between;
                        &:last-child{
                            margin-top: 5px;
                        }
                    }
                }
                .address-info{
                    flex-grow: 1;
                    flex-shrink: 1;
                    margin-left: 10px;
                    margin-right: 10px;
                    div{
                        &:first-child{
                            display: flex;
                            justify-content: space-between;
                        }
                    }
                }
            }
            .reviewInfo-container-h{
                display: flex;
                justify-content: space-between;
                padding-top: 10px;
                background-color: #f5f5f5;
                span{
                    font-size: 14px;
                    flex-grow: 1;
                    flex-shrink: 1;
                    background-color: #fff;
                    padding: 5px 0;
                    border-top: 1px solid #ccc;
                    &:first-child{
                        padding-left: 10px;
                    }
                    &:last-child{
                        padding-right: 10px;
                        font-size: 12px;
                        color: #666;
                        text-align: right;
                    }
                }
            }
            .reviewInfo-files{
                background-color: #f5f5f5;
                >div{
                    float: left;
                }
                 .file-name{
                     margin-left: 10px;
                     font-size: 12px;
                     padding-top: 10px;
                 }
                 .file-list{
                    width: 58px;
                    height: 58px;
                    margin: 10px 0 10px 10px;
                    img{
                        display: block;
                        width: 100%;
                    }
                 }
            }
            .reviewInfo-container-c{
                display: flex;
                font-size: 12px;
                line-height: 1.5em;
                background-color: #f5f5f5;
                .reviewInfo-l{
                    flex-basis: 65px;
                    flex-shrink: 0;
                    height: 65px;
                    margin: 10px;
                    img{
                        display: block;
                        width: 100%;
                    }
                }
                .reviewInfo-m{
                    flex-grow: 1;
                    flex-shrink: 1;
                    margin: 8px 0 10px 0;
                    span{
                        display: block;
                    }
                }
                .reviewInfo-r{
                    flex-basis: 50px;
                    flex-shrink: 0;
                    margin-top: 10px;
                    margin-right: 10px;
                    span{
                        display: block;
                        text-align: right;
                    }
                }
            }
            .reviewInfo-container-b{
                display: flex;
                justify-content: space-between;
                background-color: #fff;
                font-size: 12px;
                padding: 10px 0 10px 0;
                .reviewInfo-container-b-l{
                    padding-left: 10px;
                    flex-grow: 1;
                    .payType{
                        padding: 5px 0;
                    }
                }
                .reviewInfo-container-b-r{
                    padding-right: 10px;
                    display: flex;
                    flex-direction: column;
                    justify-content: space-around;
                    text-align: center;
                }
            }
            .reviewInfo-group{
                display: flex;
                font-size: 14px;
                align-items: center;
                background-color: #f5f5f5;
                padding-top: 10px;
                >div{
                    background-color: #fff;
                    border-top: 1px solid #ccc;
                    border-bottom: 1px solid #ccc;
                }
                .weui-cells_checkbox{
                    display: flex;
                }
                .weui-cells{
                    &:before{
                        border-top: none;
                    }
                    &:after{
                        border-bottom: none;
                    }
                }
                .weui-cell{
                    font-size: 14px;
                    &:before{
                        border-top: none;
                    }
                }
                input{
                    border: none;
                    outline: none;
                    line-height: 43px;
                    width: 100%;
                }
                .right{
                    display: block;
                    width: 22px;
                    height: 22px;
                    background-image: url('../../../../assets/img/right.png');
                    background-size: cover;
                    float: right;
                    margin-top: 10px;
                }
            }
        }
        footer{
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 45px;
            background-color: #64C0F4;
            line-height: 45px;
            text-align: center;
            color: #fff;
        }
    }
</style>