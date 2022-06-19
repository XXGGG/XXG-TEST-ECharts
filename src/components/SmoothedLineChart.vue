<template>
    <div id="SmoothedLineChart_1" class="ECharts"></div>
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
    data: Array<any>
}>()

onMounted(() => {
    var chartDom = document.getElementById('SmoothedLineChart_1')!;
    var myChart = echarts.init(chartDom);
    var option: EChartsOption;
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
                data: [820, 932, 901, 934, 1290, 1330, 1320],
                type: 'line',
                smooth: true
            }
        ]
    };

    option && myChart.setOption(option);
})


</script>

<style scoped>
.ECharts {
    width: 100%;
    height: 100%;
    min-width: 100px;
    min-height: 100px;
}
</style>