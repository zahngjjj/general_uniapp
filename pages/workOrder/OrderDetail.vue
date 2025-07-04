<template>
  <view class="container">
    <!-- 标题栏 -->
    <view class="header">
      <text class="header-title">工单详情</text>
    </view>
    
    <view class="header-info">
      <!-- 工单号单独一行，排在第一位 -->
      <view class="header-row">
        <text class="header-label">工单号:</text>
        <text class="header-value">{{ orderInfo.orderNo }}</text>
      </view>
      
      <!-- 产品名称单独一行，排在第二位 -->
      <view class="header-row">
        <text class="header-label">产品名称:</text>
        <text class="header-value">{{ orderInfo.productName }}</text>
      </view>
      
      <!-- 客户单独一行，排在第三位 -->
      <view class="header-row">
        <text class="header-label">客    户:</text>
        <text class="header-value">{{ orderInfo.customer }}</text>
      </view>
      
      <!-- 订单日期和交货日期一行，排在第四位 -->
      <view class="header-row">
        <text class="header-label">订单日期:</text>
        <text class="header-value">{{ orderInfo.orderDate }}</text>
        <text class="header-label right-label">交货日期:</text>
        <text class="header-value">{{ orderInfo.deliveryDate }}</text>
      </view>
      
      <!-- 订单数量和入库数量一行，排在第五位 -->
      <view class="header-row">
        <text class="header-label">订单数量:</text>
        <text class="header-value">{{ orderInfo.quantity }}</text>
        <text class="header-label right-label">入库数量:</text>
        <text class="header-value">{{ orderInfo.inStockQuantity }}</text>
      </view>
    </view>
    
    <!-- 工序进度表格 -->
    <view class="table-container">
      <view class="table-header">
        <view class="th">工序</view>
        <view class="th">计划数量</view>
        <view class="th">完工数量</view>
        <view class="th">完成率</view>
      </view>
      
      <view class="table-body">
        <view class="table-row" v-for="(item, index) in processList" :key="index">
          <view class="td">{{ item.name }}</view>
          <view class="td">{{ item.planQuantity }}</view>
          <view class="td">{{ item.completedQuantity }}</view>
          <view class="td" :class="getCompletionClass(item.completionRate)">{{ item.completionRate }}%</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      orderInfo: {
        orderNo: 'JG-2025-0001',
        customer: '客户A',
        orderDate: '2025-12-01',
        deliveryDate: '2025-12-25',
        productName: '卷烟包装',
        quantity: 500,
        inStockQuantity: 0
      },
      processList: [
        { name: '印刷', planQuantity: 500, completedQuantity: 150, completionRate: 30 },
        { name: '裱门', planQuantity: 500, completedQuantity: 0, completionRate: 0 },
        { name: '喷码', planQuantity: 500, completedQuantity: 0, completionRate: 0 },
        { name: '烫金', planQuantity: 500, completedQuantity: 0, completionRate: 0 },
        { name: '模切', planQuantity: 500, completedQuantity: 0, completionRate: 0 },
        { name: '品检', planQuantity: 500, completedQuantity: 0, completionRate: 0 },
        { name: '包装', planQuantity: 500, completedQuantity: 0, completionRate: 0 }
      ]
    };
  },
  onLoad(options) {
    // 获取传递的工单号
    if (options.orderNo) {
      this.loadOrderDetail(options.orderNo);
    }
  },
  methods: {
    // 返回上一页
    goBack() {
      uni.navigateBack();
    },
    
    // 加载工单详情
    loadOrderDetail(orderNo) {
      // 实际应用中，这里应该调用API获取工单详情
      console.log('加载工单详情:', orderNo);
      // 模拟数据加载
      // this.orderInfo = ...
      // this.processList = ...
    },
    
    // 根据完成率返回对应的CSS类名
    getCompletionClass(rate) {
      if (rate >= 100) return 'green';
      if (rate >= 50) return 'yellow';
      if (rate > 0) return 'red';
      return 'gray';
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

/* 添加标题栏样式 */
.header {
  background-color: #ffffff;
  color: #333333;
  padding: 25rpx 30rpx;
  margin: 20rpx 0; /* 上下增加间距 */
  font-weight: bold;
  border-radius: 8rpx; /* 添加圆角 */
  box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.05); /* 添加轻微阴影 */
}

.header-title {
  font-size: 36rpx;
  font-weight: bold;
  color: #333;
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
  background-color: #4285f4;
  border-radius: 3rpx;
}

/* 修改原来的header为header-info */
.header-info {
  padding: 20rpx;
  background-color: #ffffff;
  margin: 0 20rpx 20rpx;
  border-radius: 8rpx;
  box-shadow: 0 2rpx 6rpx rgba(0, 0, 0, 0.05);
}

/* 其他样式保持不变 */
.header-row {
  display: flex;
  padding: 10rpx 0;
  flex-wrap: wrap;
}

.header-label {
  width: 160rpx;
  color: #666666;
  font-size: 28rpx;
}

.right-label {
  margin-left: 40rpx;
}

.header-value {
  flex: 1;
  color: #333333;
  font-size: 28rpx;
  font-weight: 500;
}

/* 表格容器 */
.table-container {
  margin: 20rpx;
  border-radius: 8rpx;
  overflow: hidden;
  background-color: #ffffff;
  box-shadow: 0 2rpx 6rpx rgba(0, 0, 0, 0.05);
}

/* 表格头部 */
.table-header {
  display: flex;
  background-color: #f8f9fa;
  border-bottom: 1px solid #eeeeee;
}

.th {
  flex: 1;
  padding: 20rpx 10rpx;
  text-align: center;
  font-size: 28rpx;
  color: #333333;
  font-weight: bold;
}

/* 表格内容 */
.table-body {
  background-color: #ffffff;
}

.table-row {
  display: flex;
  border-bottom: 1px solid #eeeeee;
}

.table-row:last-child {
  border-bottom: none;
}

.td {
  flex: 1;
  padding: 20rpx 10rpx;
  text-align: center;
  font-size: 28rpx;
  color: #333333;
}

/* 完成率颜色 */
.green {
  color: #4caf50;
  font-weight: bold;
}

.yellow {
  color: #ff9800;
  font-weight: bold;
}

.red {
  color: #f44336;
  font-weight: bold;
}

.gray {
  color: #9e9e9e;
}
</style>