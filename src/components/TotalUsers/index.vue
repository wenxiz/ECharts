<template>
  <common-card
    title="累计用户数"
    value="1,087,503"
  >
    <template>
      <div id="total-users-chart" :style="{width: '100%', height: '100%'}" />
    </template>
    <template v-slot:footer>
      <div class="total-users-footer">
        <span>日同比</span>
        <span class="emphsis">8.73%</span>
        <div class="increase" />
        <span class="month">月同比</span>
        <span class="emphsis">35.91%</span>
        <div class="decrease" />
      </div>
    </template>
  </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'

export default {
  mixins: [commonCardMixin],
  mounted () {
    const chartDOM = document.getElementById('total-users-chart')
    const chart = this.$echarts.init(chartDOM)
    chart.setOption({
      xAxis: {
        type: 'value',
        show: false
      },
      yAxis: {
        type: 'category',
        show: false
      },
      series: [{
        type: 'bar',
        data: [200],
        barWidth: '10',
        stack: '总量',
        itemStyle: {
          color: '#45c946'
        }
      }, {
        type: 'bar',
        data: [250],
        barWidth: '10',
        stack: '总量',
        itemStyle: {
          color: '#eee'
        }
      }, {
        type: 'custom',
        data: [200],
        stack: '总量',
        renderItem: (params, api) => {
          const value = api.value(0)
          const endPoint = api.coord([value, 0])

          return {
            type: 'group',
            position: endPoint,
            children: [{
              type: 'path',
              shape: {
                d: 'M952.32 715.2l-416-485.376c-12.16-14.176-36.448-14.176-48.608 0l-416 485.376c-8.128 9.472-9.984 22.848-4.768 34.176C72.16 760.704 83.488 768 96 768h832c12.512 0 23.84-7.296 29.056-18.624s3.392-24.704-4.736-34.176z',
                x: -5,
                y: 10,
                width: 10,
                height: 10,
                layout: 'cover'
              },
              style: {
                fill: '#45c946'
              }
            }, {
              type: 'path',
              shape: {
                d: 'M957.056 338.624C951.84 327.296 940.512 320 928 320L96 320c-12.512 0-23.84 7.296-29.088 18.624-5.216 11.36-3.328 24.704 4.768 34.208l416 485.344c6.08 7.104 14.944 11.2 24.288 11.2s18.208-4.096 24.288-11.2l416-485.344C960.448 363.328 962.272 349.984 957.056 338.624z',
                x: -5,
                y: -20,
                width: 10,
                height: 10,
                layout: 'cover'
              },
              style: {
                fill: '#45c946'
              }
            }]
          }
        }
      }],
      grid: {
        top: 0,
        bottom: 0,
        left: 0,
        right: 0
      }
    })
  }
}
</script>

<style lang='scss' scoped>
  .total-users-footer {
    height: 100%;
    display: flex;
    align-items: center;
    .month {
      margin-left: 10px;
    }
  }
</style>
