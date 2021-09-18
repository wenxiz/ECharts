<template>
  <common-card
    title="累计订单量"
    value="215,420"
  >
  <template>
    <!-- 2. 创造好DOM，设定好宽高 -->
    <div id="total-order-chart" :style="{width: '100%', height: '100%'}" />
  </template>
  <template v-slot:footer>
    <span>昨日订单量 </span>
    <span class="emphsis">2,000,000</span>
  </template>
  </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'

export default {
  mixins: [commonCardMixin],
  mounted () {
    // 3. 获取渲染对象
    const chartDOM = document.getElementById('total-order-chart')
    // 4. 初始化渲染对象
    const chart = this.$echarts.init(chartDOM)
    // 5. 设置option选项
    chart.setOption({
      xAxis: {
        type: 'category',
        show: false,
        boundaryGap: false
      },
      yAxis: {
        show: false
      },
      series: [{
        type: 'line',
        data: [620, 420, 220, 532, 790, 430, 220, 320, 532, 320, 834, 690, 530, 220, 620],
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
      }],
      grid: {
        top: 0,
        bottom: 0,
        right: 0,
        left: 0
      }
    })
  }
}
</script>

<style>

</style>
