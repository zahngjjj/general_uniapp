<template>
  <view class="container">
    <!-- 标签页导航 -->
    <view class="tabs-header">
      <view 
        class="tab-item" 
        :class="{ active: activeTab === 'sales' }"
        @click="switchTab('sales')"
      >
        销售完成情况
      </view>
      <view 
        class="tab-item" 
        :class="{ active: activeTab === 'production' }"
        @click="switchTab('production')"
      >
        生产完成情况
      </view>
    </view>
    
    <!-- 标签页内容 -->
    <view class="tabs-content">
      <!-- 销售完成情况 -->
      <view v-if="activeTab === 'sales'" class="tab-content">
        <MonthlySalesChart />
      </view>
      
      <!-- 生产完成情况 -->
      <view v-if="activeTab === 'production'" class="tab-content">
        <MonthlyProductionChart />
      </view>
    </view>
  </view>
</template>

<script>
// 引入组件
import MonthlySalesChart from '../charts/MonthlySalesChart.vue';
import MonthlyProductionChart from '../charts/MonthlyProductionChart.vue';

export default {
  components: {
    MonthlySalesChart,
    MonthlyProductionChart
  },
  data() {
    return {
      activeTab: 'sales' // 默认显示销售完成情况
    };
  },
  methods: {
    // 切换标签页
    switchTab(tabName) {
      this.activeTab = tabName;
    }
  }
}
</script>

<style>
.container {
  padding: 0;
  background-color: #f5f5f5;
  min-height: 100vh;
}

/* 标签页导航样式 */
.tabs-header {
  display: flex;
  background-color: #fff;
  border-bottom: 1px solid #eee;
  position: sticky;
  top: 0;
  z-index: 10;
}

.tab-item {
  flex: 1;
  text-align: center;
  padding: 30rpx 0;
  font-size: 30rpx;
  color: #666;
  position: relative;
  transition: all 0.3s;
}

.tab-item.active {
  color: #4285f4;
  font-weight: bold;
}

/* 活动标签底部指示器 */
.tab-item.active::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 40%;
  height: 6rpx;
  background-color: #4285f4;
  border-radius: 3rpx;
}

/* 标签页内容样式 */
.tabs-content {
  padding: 20rpx;
}

.tab-content {
  background-color: #fff;
  border-radius: 10rpx;
  overflow: hidden;
  animation: fadeIn 0.3s ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10rpx);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>