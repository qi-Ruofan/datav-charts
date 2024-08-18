<template>
  <common-card :title="title" :value="value">
    <template>
      <div ref="total-orders-chart" style="width: 100%;height: 100%;"></div>
    </template>
    <template v-slot:footer>
      <span>昨日订单量</span>
      <span class="emphasis">2,000,000</span>
    </template>
  </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'
export default {
  mixins: [commonCardMixin],
  data () {
    return {
      title: '累计订单量',
      value: '2,123,223',
      option: null
    }
  },
  mounted () {
    this.initChart()
  },
  methods: {
    initChart() {
      const myChart = this.$echarts.init(this.$refs['total-orders-chart'])
      this.option = {
        color: '#80FFA5',
        series: [
          {
            type: 'line',
            data: [620, 432, 220, 534, 790, 430, 220, 320, 532, 320, 834, 690, 530, 220, 620],
            areaStyle: {
              color: 'purple'
            },
            lineStyle: {
              width: 0
            },
            itemStyle: {
              opacity: 0
            },
            smooth: true
          }
        ],
        grid: {
          bottom: 0,
          top: 0,
          left: 0,
          right: 0
        },
        xAxis: {
          type: 'category',
          show: false,
          boundaryGap: false // 与x轴两侧是否有边距
        },
        yAxis: {
          show: false
        }
      }
      myChart.setOption(this.option)
    }
  }
}
</script>
