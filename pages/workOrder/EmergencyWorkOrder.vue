<template>
  <view class="container">
    <view class="header">
      <text class="header-title">紧急工单跟踪</text>
    </view>
    
    <!-- 工单卡片列表 -->
    <view class="order-list">
      <view class="order-card" v-for="(item, index) in workOrderList" :key="index" @click="navigateToDetail(item)">
        <view class="order-header">
          <text class="order-id">{{ item.orderNo }}</text>
          <text class="completion-rate" :class="getCompletionClass(item.completionRate)">{{ item.completionRate }}%</text>
        </view>
        
        <view class="order-info">
          <view class="info-row">
            <text class="info-label">客    户:</text>
            <text class="info-value">{{ item.customer }}</text>
          </view>
          
          <view class="info-row">
            <text class="info-label">交货日期:</text>
            <text class="info-value">{{ item.deliveryDate }}</text>
          </view>
          
          <view class="info-row">
            <text class="info-label">工单数量:</text>
            <text class="info-value">{{ item.quantity }}</text>
          </view>
        </view>
        
        <view class="order-footer">
          <text class="arrow-icon">›</text>
        </view>
      </view>
      
      <!-- 空数据展示 -->
      <view class="empty-data" v-if="workOrderList.length === 0">
        <text>暂无紧急工单数据</text>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      workOrderList: [
        { orderNo: 'JG-2025-0001', customer: '客户A', deliveryDate: '2025-12-25', quantity: 500, completionRate: 85 },
        { orderNo: 'JG-2025-0002', customer: '客户B', deliveryDate: '2025-12-26', quantity: 300, completionRate: 100 },
        { orderNo: 'JG-2025-0003', customer: '客户C', deliveryDate: '2025-12-27', quantity: 800, completionRate: 65 },
        { orderNo: 'JG-2025-0004', customer: '客户D', deliveryDate: '2025-12-28', quantity: 200, completionRate: 90 }
      ]
    };
  },
  methods: {
    // 根据完成率返回对应的CSS类名
    getCompletionClass(rate) {
      if (rate >= 100) return 'green';
      if (rate >= 80) return 'yellow';
      if (rate > 0) return 'red';
      return 'gray';
    },
    
    // 导航到详情页
    navigateToDetail(item) {
      // 这里可以添加导航逻辑
      console.log('查看工单详情:', item.orderNo);
    }
  }
};
</script>

<style scoped>
.container {
  padding: 0;
  background-color: #f5f5f5;
  min-height: 100vh;
  color: #333333;
}

.header {
  padding: 25rpx 30rpx;
  margin-bottom: 10rpx;
  border-bottom: 1px solid #eeeeee;
  background-color: #ffffff;
}

.header-title {
  font-size: 36rpx;
  font-weight: bold;
  color: #333333;
  position: relative;
  padding-left: 20rpx;
  display: inline-block;
}

/* 添加左侧装饰线 */
.header-title::before {
  content: "";
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 6rpx;
  height: 32rpx;
  background-color: #1890ff;
  border-radius: 3rpx;
}

/* 工单列表 */
.order-list {
  padding: 20rpx;
}

/* 工单卡片样式 */
.order-card {
  background-color: #ffffff;
  border-radius: 10rpx;
  overflow: hidden;
  margin-bottom: 20rpx;
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.1);
  animation: fadeIn 0.5s ease-in-out;
  position: relative;
}

/* 工单卡片头部 */
.order-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20rpx 30rpx;
  border-bottom: 1px solid #eeeeee;
}

.order-id {
  font-size: 32rpx;
  font-weight: bold;
  color: #1890ff;
}

.completion-rate {
  padding: 6rpx 20rpx;
  border-radius: 30rpx;
  font-size: 26rpx;
  font-weight: bold;
}

/* 工单信息 */
.order-info {
  padding: 20rpx 30rpx;
}

.info-row {
  display: flex;
  margin-bottom: 16rpx;
}

.info-row:last-child {
  margin-bottom: 0;
}

.info-label {
  width: 160rpx;
  color: #666666;
  font-size: 28rpx;
}

.info-value {
  flex: 1;
  color: #333333;
  font-size: 28rpx;
}

/* 工单底部 */
.order-footer {
  display: flex;
  justify-content: flex-end;
  padding: 10rpx 30rpx;
  border-top: 1px solid #eeeeee;
}

.arrow-icon {
  font-size: 40rpx;
  color: #cccccc;
}

/* 完成率颜色 */
.green {
  background-color: rgba(76, 175, 80, 0.2);
  color: #4caf50;
}

.yellow {
  background-color: rgba(255, 152, 0, 0.2);
  color: #ff9800;
}

.red {
  background-color: rgba(244, 67, 54, 0.2);
  color: #f44336;
}

.gray {
  background-color: rgba(158, 158, 158, 0.2);
  color: #9e9e9e;
}

/* 空数据提示 */
.empty-data {
  padding: 60rpx 0;
  text-align: center;
  color: #999999;
  font-size: 28rpx;
}

/* 添加渐入动画 */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>