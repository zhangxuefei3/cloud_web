<template>
  <div class="Echarts">
    <div id="main" style="width:600px;height:300px"></div>
  </div>
</template>

<script>
export default {
  name: 'Echarts',
  // data() {
  //   return {

  //   }
  // },
  mounted() {
    this.$nextTick(() => {
      this.myEcharts()
    })
  },
  methods: {
    myEcharts() {
      // 初始化echarts实例
      var myChart = this.$echarts.init(document.getElementById('main'))
      // 指定配置项和数据
      var option = {
        // title: {
        //   text: '仿真结果'
        // },
        // tooltip: {},
        // legend: {
        //   data: ['Step End']
        // },
        // xAxis: {
        //   // type: 'value',
        //   // data: [1, 2, 3, 4, 5, 6, 7]
        //   type: 'category',
        //   data: ['1', '2', '3', '4', '5', '6', '7']
        // },
        // yAxis: {
        //   // type = 'value'
        // },
        // series: [
        //   {
        //     name: 'step end',
        //     type: 'line',
        //     step: 'end',
        //     // data: []
        //     data: [120, 132, 101, 134, 90, 230, 210]
        //   }
        // ]
        title: {
          text: 'Step Line'
        },
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          data: ['Step Start', 'Step Middle', 'Step End']
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        toolbox: {
          feature: {
            saveAsImage: {}
          }
        },
        xAxis: {
          type: 'category',
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        yAxis: {
          type: 'value'
        },
        series: [
          {
            name: 'Step Start',
            type: 'line',
            step: 'start',
            data: [120, 132, 101, 134, 90, 230, 210]
          },
          {
            name: 'Step Middle',
            type: 'line',
            step: 'middle',
            data: [220, 282, 201, 234, 290, 430, 410]
          },
          {
            name: 'Step End',
            type: 'line',
            step: 'end',
            data: [450, 432, 401, 454, 590, 530, 510]
          }
        ]
      }
      myChart.setOption(option)
      window.addEventListener('resize', function() {
        this.option.myChart.resize()
      })
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
