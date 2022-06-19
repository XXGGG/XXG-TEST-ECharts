<template>
    <div id="BasicLineChart_1"  class="ECharts"></div>
</template>

<script setup lang='ts'>
import { onMounted } from 'vue';
import * as echarts from 'echarts/core';
import { GridComponent, GridComponentOption } from 'echarts/components';
import { LineChart, LineSeriesOption } from 'echarts/charts';
import { UniversalTransition } from 'echarts/features';
import { CanvasRenderer } from 'echarts/renderers';
echarts.use([GridComponent, LineChart, CanvasRenderer, UniversalTransition]);
type EChartsOption = echarts.ComposeOption<
    GridComponentOption | LineSeriesOption
>;

const props = defineProps<{
    data:Array<any>
}>()

onMounted(() => {
    var chartDom = document.getElementById('BasicLineChart_1')!;
    var myChart = echarts.init(chartDom);
    var option: EChartsOption;
    // option= props.data;
    // option = {
    //     xAxis: {
    //         type: 'category',
    //         data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    //     },
    //     yAxis: {
    //         type: 'value'
    //     },
    //     series: [
    //         {
    //             data: [150, 230, 224, 218, 135, 147, 260],
    //             type: 'line'
    //         }
    //     ]
    // };
    option = {
        xAxis: {
            type: 'category',
            data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        yAxis: {
            type: 'value'
        },
        series: [
            {
                data: props.data,
                type: 'line'
            }
        ]
    };
    option && myChart.setOption(option);
})





</script>

<style scoped>
.ECharts{
    width: 100%;
    height: 100%;
    min-width: 100px;
    min-height: 100px;
}
</style>