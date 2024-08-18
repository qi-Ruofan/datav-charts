<template>
  <common-card :title="title" :value="value">
    <template>
      <div ref="total-users-chart" style="width: 100%;height: 100%;"></div>
    </template>
    <template v-slot:footer>
      <div class="total-users-footer">
        <span>日同比</span>
        <span class="emphasis">6.93%</span>
        <span class="increase"></span>
        <span class="month">月同比</span>
        <span class="emphasis">33.66%</span>
        <span class="decrease"></span>
      </div>
    </template>
  </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'
export default {
  mixins: [commonCardMixin],
  data () {
    return {
      title: '累计用户数',
      value: '1,070,265',
      option: null
    }
  },
  mounted () {
    this.initChart()
  },
  methods: {
    initChart() {
      const myChart = this.$echarts.init(this.$refs['total-users-chart'])
      this.option = {
        series: [
          {
            type: 'bar',
            // stack: '总量', // 合并
            data: [200],
            barWidth: 10,
            itemStyle: {
              color: '#45c946'
            }
          },
          {
            z: '-1',
            barGap: '-100%', // 不同系列的柱间距离，为百分比
            type: 'bar',
            // stack: '总量',// 合并
            data: [250],
            barWidth: 10,
            itemStyle: {
              color: '#eee'
            }
          },
          {
            type: 'custom',
            barGap: '-100%',
            data: [200],
            renderItem: (params, api) => {
              const value = api.value(0) // 获取data[0]
              const endPoint = api.coord([value, 0])
              return {
                type: 'group',
                position: endPoint,
                children: [
                  {
                    type: 'path',
                    shape: {
                      d: 'M793.002667 341.333333H230.997333a42.666667 42.666667 0 0 0-30.165333 72.832l281.002667 281.002667a42.666667 42.666667 0 0 0 60.330666 0l281.002667-281.002667A42.752 42.752 0 0 0 793.002667 341.333333z',
                      x: -6,
                      y: -18,
                      width: 10,
                      height: 10,
                      layout: 'cover'
                    },
                    style: {
                      fill: '#45c946'
                    }
                  },
                  {
                    type: 'path',
                    shape: {
                      d: 'M542.165333 328.832a42.666667 42.666667 0 0 0-60.330666 0l-281.002667 281.002667A42.752 42.752 0 0 0 230.997333 682.666667h562.005334a42.666667 42.666667 0 0 0 30.165333-72.832l-281.002667-281.002667z',
                      x: -6,
                      y: 7,
                      width: 10,
                      height: 10,
                      layout: 'cover'
                    },
                    style: {
                      fill: '#45c946'
                    }
                  }
                ]
              }
            }
          }
        ],
        grid: {
          bottom: 0,
          top: 0,
          left: 0,
          right: 0
        },
        xAxis: {
          type: 'value',
          show: false,
          boundaryGap: false // 与x轴两侧是否有边距
        },
        yAxis: {
          type: 'category',
          show: false
        }
      }
      myChart.setOption(this.option)
    }
  }
}
</script>

<style lang='scss' scoped>
.total-users-footer {
  display: flex;
  align-items: center;
  .month {
    margin-left: 10px;
  }
}
</style>
