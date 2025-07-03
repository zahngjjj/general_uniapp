<template>
  <view class="container">
    <view class="chart-container">
      <view class="chart-title">销售</view>
      <!-- 替换为秋云图表组件 -->
      <qiun-data-charts 
        type="mix"
        :opts="opts"
        :chartData="chartData"
        canvasId="salesChart"
      />
    </view>
  </view>
</template>

<script>
// 引入秋云图表组件
import qiunDataCharts from '@qiun/ucharts-mp';

export default {
  components: {
    qiunDataCharts
  },
  data() {
    return {
      // 图表配置
      opts: {
        color: ['#f8b195', '#7a9ee0', '#f3c13a'],
        padding: [15, 15, 0, 15],
        legend: {
          show: true,
          position: 'bottom',
          float: 'center'
        },
        xAxis: {
          disableGrid: true
        },
        yAxis: {
          data: [
            {
              min: 0,
              max: 6,
              splitNumber: 6
            }
          ]
        },
        extra: {
          column: {
            width: 30,
            barBorderRadius: 0
          },
          line: {
            width: 3,
            type: 'straight'
          }
        }
      },
      // 图表数据
      chartData: {
        categories: ['1', '2', '3', '4'],
        series: [
          {
            name: '目标',
            type: 'column',
            data: [4.2, 2.5, 3.5, 4.3]
          },
          {
            name: '实际',
            type: 'column',
            data: [2.1, 2.2, 3.0, 4.9]
          },
          {
            name: '完成比例',
            type: 'line',
            data: [2.5, 4.3, 1.8, 2.9],
            style: 'curve', // 曲线样式
            pointShape: 'circle' // 点的形状
          }
        ]
      }
    };
  }
}
</script>

<style>
.container {
  padding: 20rpx;
}
.chart-container {
  background-color: #fff;
  border-radius: 10rpx;
  box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.1);
  padding: 20rpx;
  margin-bottom: 20rpx;
}
.chart-title {
  font-size: 32rpx;
  font-weight: bold;
  text-align: center;
  margin-bottom: 20rpx;
}
/* 设置图表容器高度 */
.qiun-charts {
  width: 100%;
  height: 600rpx;
}
</style>