<template>
  <div id="main" style="width: 600px;height: 400px;margin:0 auto;" ref="selfEchart"></div>
</template>

<script>
import axios from 'axios'
export default {
    created () {
        this.fetchSourceData()
    },
    mounted () {
        this.initChart()
    },
    methods: {
        initChart () {
      // 基于准备好的dom,初始化eChars实例
            var myChart = this.$echarts.init(this.$refs.selfEchart)
      // 指定图表的配置项和数据
            var option = {
                title: {
                    text: 'ECharts 入门示例'
                },
                tooltip: {
                    trigger: 'axis',
                    axisPointer: {
                        type: 'cross',
                        crossStyle: {
                            color: '#999'
                        }
                    }
                },
                legend: {
                    data: ['销量', '单价']
                },
                xAxis: {
                    data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子'],
                    axisPointer: {
                        type: 'shadow'
                    }
                },
                yAxis: [
                    {
                        type: 'value',
                        name: '销量',
                        min: 0,
                        max: 50,
                        interval: 10,
                        axisLabel: {
                            formatter: '{value} 件'
                        }
                    },
                    {
                        type: 'value',
                        name: '批发价',
                        min: 0,
                        max: 50,
                        interval: 10,
                        axisLabel: {
                            formatter: '{value} RMB'
                        }
                    }],
                series: [{
                    name: '销量',
                    type: 'bar',
                    data: [5, 20, 36, 46, 20, 30]
                }, {
                    name: '单价',
                    type: 'line',
                    data: [10, 23, 16, 26, 30, 16]
                }]
            }
      // 使用刚指定的配置项和数据显示图表
            myChart.setOption(option)
        },
        fetchSourceData () {
            console.log('mock')
            axios.get('http://localhost:8088/getResource').then((res) => {
                console.log(res)
            })
        }

    }

}
</script>

<style>

</style>
