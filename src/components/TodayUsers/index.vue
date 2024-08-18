<template>
  <common-card :title="title" :value="value">
    <template>
      <div ref="today-users-chart" style="width: 100%;height: 100%;"></div>
    </template>
    <template v-slot:footer>
      <span>退货率</span>
      <span class="emphasis">5.02%</span>
    </template>
  </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'
export default {
  mixins: [commonCardMixin],
  data () {
    return {
      title: '今日交易用户数',
      value: '累计用户数',
      option: null
    }
  },
  mounted () {
    this.initChart()
  },
  methods: {
    initChart() {
      const myChart = this.$echarts.init(this.$refs['today-users-chart'])
      this.option = {
        color: '#3398DB',
        series: [
          {
            type: 'bar',
            data: [620, 432, 220, 534, 790, 430, 220, 320, 532, 320, 834, 690, 530, 220],
            barWidth: '60%'
          }
        ],
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'line'
          }
        },
        grid: {
          bottom: 0,
          top: 0,
          left: 0,
          right: 0
        },
        xAxis: {
          type: 'category',
          show: false,
          data: ['00:00','01:00','02:00','03:00','04:00','05:00','06:00','07:00','08:00','09:00','10:00','11:00','12:00','13:00']
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
