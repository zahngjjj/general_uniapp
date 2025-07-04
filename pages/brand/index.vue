<template>
  <view class="container">
    <view class="header">
      <text class="header-title">年品牌完成率</text>
    </view>
    
    <!-- 表格 -->
    <view class="table-container">
      <table class="data-table">
        <tr>
          <th>品牌名称</th>
          <th>品牌目标</th>
          <th>配套烟箱</th>
          <th>完成率</th>
        </tr>
        <tr v-for="(item, index) in tableData" :key="index" :class="{'highlight': item.ratio > 100}">
          <td>{{ item.name }}</td>
          <td>{{ item.target }}</td>
          <td>{{ item.actual }}</td>
          <td :class="getCompletionClass(item.ratio)">{{ item.ratio }}%</td>
        </tr>
      </table>
    </view>
  </view>
</template>
  
<script>
export default {
  data() {
    return {
      tableData: [
        { name: "双喜(硬经典1906)", target: "215,000", actual: "124,164", ratio: 57.75 },
        { name: "双喜(新版花悦)(喷码)", target: "40,000", actual: "15,386", ratio: 38.47 },
        { name: "真龙(软妍子)", target: "0", actual: "8,541", ratio: 0.00 },
        { name: "双喜(喜粤)", target: "5,000", actual: "5,206", ratio: 104.13 },
        { name: "白沙(软和天下)", target: "10,291", actual: "3,823", ratio: 37.15 },
        { name: "玉溪(软阿诗玛)(GD HT5.1版)", target: "0", actual: "3,440", ratio: 0.00 },
        { name: "普通红双喜精装硬盒", target: "5,000", actual: "3,009", ratio: 60.18 },
        { name: "白沙(利事)", target: "5,000", actual: "1,905", ratio: 38.09 },
        { name: "阿里山景泰典蓝(蓝莓宝珠)", target: "40,000", actual: "1,844", ratio: 4.61 },
        { name: "白沙(硬和天下双中支)", target: "3,750", actual: "1,283", ratio: 34.20 },
        { name: "双喜(盛世)", target: "6,000", actual: "653", ratio: 10.89 },
        { name: "16106 GDX1黄鹤楼(软雪之景)", target: "0", actual: "574", ratio: 0.00 },
        { name: "龙凤呈祥(硬)", target: "0", actual: "309", ratio: 0.00 },
        { name: "双喜(国喜细支)", target: "4,000", actual: "296", ratio: 7.41 },
        { name: "烟模", target: "0", actual: "1", ratio: 0.00 }
      ]
    };
  },
  methods: {
    // 根据完成率返回对应的CSS类名
    getCompletionClass(ratio) {
      if (ratio >= 100) return 'green';
      if (ratio >= 50) return 'yellow';
      if (ratio > 0) return 'red';
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

/* 表格样式 */
.table-container {
  margin: 14rpx 12rpx;
  padding: 0;
  background-color: #fff;
  border-radius: 8rpx;
  overflow: hidden;
  box-shadow: 0 2rpx 10rpx rgba(0, 0, 0, 0.05);
  animation: fadeIn 0.8s ease-in-out;
}

.data-table {
  width: 100%;
  border-collapse: collapse;
  text-align: center;
  background-color: #ffffff;
  color: #333333;
  font-size: 28rpx;
}

.data-table th, .data-table td {
  border: 1px solid #eeeeee;
  padding: 12rpx 8rpx;
}

.data-table th {
  background-color: #f8f9fa;
  color: #333333;
  font-weight: bold;
  position: sticky;
  top: 0;
  z-index: 10;
}

.data-table tr {
  transition: background-color 0.3s;
}

.data-table tr:nth-child(even) {
  background-color: #f9f9f9;
}

.data-table tr:hover {
  background-color: #f0f7ff;
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
  color: #ff5252;
  font-weight: bold;
}

.gray {
  color: #9e9e9e;
}

/* 高亮超额完成的行 */
.highlight {
  background-color: rgba(76, 175, 80, 0.08) !important;
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