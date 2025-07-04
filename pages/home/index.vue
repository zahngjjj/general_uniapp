<template>
  <view class="container">
    <!-- 标题栏 -->
    <view class="header">
      <text class="header-title">目标完成情况</text>
    </view>
    
    <!-- 数据卡片区域 -->
    <view class="cards-container">
      <!-- 第一行卡片：年度相关指标 -->
      <view class="cards-row">
        <view class="card">
          <text class="card-title">年度目标</text>
          <text class="card-value blue">10,000</text>
        </view>
        <view class="card">
          <text class="card-title">年度完成数量</text>
          <text class="card-value blue">8,500</text>
        </view>
        <view class="card">
          <text class="card-title">年度完成率</text>
          <text class="card-value red">85.0%</text>
        </view>
      </view>
      
      <!-- 第二行卡片：月度相关指标 -->
      <view class="cards-row">
        <view class="card">
          <text class="card-title">月度目标</text>
          <text class="card-value blue">1,000</text>
        </view>
        <view class="card">
          <text class="card-title">月度完成数量</text>
          <text class="card-value blue">950</text>
        </view>
        <view class="card">
          <text class="card-title">月度完成率</text>
          <text class="card-value orange">95.0%</text>
        </view>
      </view>
      
      <!-- 第三行卡片：质量相关指标 -->
      <view class="cards-row">
        <view class="card">
          <text class="card-title">年度质量目标</text>
          <text class="card-value blue">98.0%</text>
        </view>
        <view class="card">
          <text class="card-title">实际合格率</text>
          <text class="card-value blue">97.5%</text>
        </view>
        <view class="card empty-card"></view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      // 数据可以根据实际需求从API获取
    };
  },
  onReady() {
    // 页面加载完成后的处理
  },
  methods: {
    // 方法定义
  }
};
</script>

<style scoped>
  /* 整体容器样式 */
  .container {
    width:100%;
    height:calc(100dvh - 114px);
    background-color: #f5f5f5;
  }
  
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
  
  /* 卡片容器样式 */
  .cards-container {
    margin-bottom: 30rpx;
	padding: 10px;
  }
  
  .cards-row {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20rpx;
    border: none; /* 移除边框 */
    background-color: transparent; /* 背景透明 */
    border-radius: 8rpx; /* 添加圆角 */
    overflow: hidden; /* 确保子元素不超出圆角边界 */
    box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.05); /* 添加轻微阴影 */
  }
  
  
  /* 卡片样式 */
  .card {
    flex: 1;
    background-color: #ffffff;
    color: #333333;
    padding: 20rpx 10rpx;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border-right: 1px solid #eeeeee;
    min-height: 160rpx;
	transition: all 0.3s ease; /* 添加过渡效果 */
  }
  
  .card:last-child {
    border-right: none;
  }
  
  .card-title {
    font-size: 28rpx;
    margin-bottom: 10rpx;
    text-align: center;
  }
  
  .card-value {
    font-size: 48rpx;
    font-weight: bold;
    text-align: center;
  }
  
  .blue {
    color: #4285f4; /* 更现代的蓝色 */
  }
  
  .red {
    color: #ea4335; /* 更现代的红色 */
  }
  
  .orange {
    color: #fbbc05; /* 更现代的橙色 */
  }
  
  .empty-card {
    background-color: #ffffff;
    border: none;
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
  
  /* 为卡片添加动画 */
  .cards-container {
    animation: fadeIn 0.8s ease-in-out;
  }
</style>