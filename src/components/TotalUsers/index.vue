<template>
    <div>
        <common-card 
        title="累计用户数"
        value="1,087,503"
        >
        <template>
            <div id="total-users-chart" :style="{ width:'100%',height:'100%' }" />
        </template>
        <template v-slot:footer>
        <div class="total-users-footer">
            <span>日同比 </span>
            <span class="emphasis">8.73%</span>
            <div class="increase" />
            <span class="month">月同比 </span>
            <span class="emphasis">35.91%</span>
            <div class="decrease" />
        </div>
        </template>
        </common-card>
    </div>
</template>

<script>
import commonCardMixin from "@/mixins/commonCardMixin";

    export default {
        mixins:[commonCardMixin],
        mounted() {
            const chartDom = document.getElementById('total-users-chart')
            const chart = this.$echarts.init(chartDom)
            chart.setOption({
                grid:{
                    top:0,
                    bottom:0,
                    left:0,
                    right:0
                },
                xAxis:{
                    type:'value',
                    show:false
                },
                yAxis:{
                    type:'category',
                    show:false
                },
                series:[{
                    type:'bar',
                    stack:'总量',
                    data:[100],
                    barWidth:10,
                    itemStyle:{
                        color:'#45c946'
                    }
                },{
                    type:'bar',
                    stack:'总量',
                    data:[150],
                    itemStyle:{
                        color:'#eee'
                    }
                },{
                    type:'custom',
                    data:[100],
                    renderItem:(params,api) => {
                        const value = api.value(0)
                        const endPoint = api.coord([value,0])

                        return{
                            type:'group',
                            position:endPoint,
                            children:[{
                                type:'path',
                                shape:{
                                d:'M951.1626 819.412438 72.8374 819.412438 511.999488 204.586538Z',
                                x:-5,
                                y:9,
                                width:10,
                                height:10,
                                layout:'cover'
                                },
                                style:{
                                fill:'#45c946'
                                }
                            },{
                                type:'path',
                                shape:{
                                d:'M511.999488 819.413462 72.8374 204.586538 951.1626 204.586538Z',
                                x:-5,
                                y:-19,
                                width:10,
                                height:10,
                                layout:'cover'
                                },
                                style:{
                                fill:'#45c946'
                                }
                            }]

                        }
                    }
                }]
            })
        },
    }
</script>
<style lang="scss" scoped>
.total-users-footer{
    display:flex;
    align-content: center;
    .month{
        margin-left: 10px;
    }
}
</style>