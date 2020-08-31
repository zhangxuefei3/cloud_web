<template>
  <div class="Echarts">
    <!-- <div id="myChart" style="width:700px;height:300px"></div> -->
    <div id="myChart"></div>
  </div>
</template>

<script>
export default {
  name: 'Echarts',
  computed: {
    Option () {
      return {
        // 指定配置项和数据
        title: {
          text: '仿真结果'
        },
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          data: ['Step End', 'Step End1']
        },
        grid: {
          x: 80,
          y: 60,
          x2: 80,
          y2: 60,
          backgroundColor: 'rgba(0,0,0,0)',
          borderWidth: 1,
          borderColor: '#ccc'
        },
        xAxis: {
          // type: 'value',
          // data: [1, 2, 3, 4, 5, 6, 7]
          type: 'category',
          data: ['1', '2', '3', '4', '5', '6', '7']
        },
        yAxis: {
          // type = 'value'
        },
        series: [
          {
            name: 'Step End',
            type: 'line',
            step: 'end',
            // data: []
            data: [120, 132, 101, 134, 90, 230, 210]
          },
          {
            name: 'Step End1',
            type: 'line',
            step: 'end',
            data: [450, 432, 401, 454, 590, 530, 510]
          }
        ]
      }
    }
  },
  data() {
    return {
      myChart: null
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.myEcharts()
    })
  },

  methods: {
    myEcharts() {
      // 初始化echarts实例
      var myChart = this.$echarts.init(document.getElementById('myChart'))
      myChart.setOption(this.Option)
      window.addEventListener('resize', function() {
        if (myChart) {
          myChart.resize()
        }
        // myChart.resize()
      })
    }
  }
}
</script>

<style lang="scss" scoped>
  #myChart
  {
    width: 85%;
    height: 320px;
  }
</style>
