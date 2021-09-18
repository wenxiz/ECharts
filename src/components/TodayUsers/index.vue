<template>
  <common-card
    title="今日交易用户数"
    value="81,014"
  >
    <template>
      <!-- 2. 渲染DOM及宽高 -->
      <div id="today-users-chart" :style="{width: '100%', height: '100%'}"></div>
    </template>
    <template v-slot:footer>
      <span>退货率 </span>
      <span class="emphsis">5.14%</span>
    </template>
  </common-card>
</template>

<script>
import commonCardMixin from '../../mixins/commonCardMixin'

export default {
  mixins: [commonCardMixin],
  mounted () {
    // 3. 获取DOM节点
    const chartDOM = document.getElementById('today-users-chart')
    // 4. 初始化DOM节点
    const chart = this.$echarts.init(chartDOM)
    // 5. 设置chartOptions
    chart.setOption({
      xAxis: {
        type: 'category',
        show: false,
        data: ['00:00', '01:00', '02:00', '03:00', '04:00', '05:00', '06:00', '07:00', '08:00', '09:00', '10:00', '11:00', '12:00', '13:00', '14:00']
      },
      yAxis: {
        show: false
      },
      series: [{
        type: 'bar',
        barWidth: '60%',
        data: [410, 82, 200, 334, 390, 330, 220, 150, 82, 200, 134, 290, 330, 150]
      }],
      color: ['#3398DB'],
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

<style>

</style>
