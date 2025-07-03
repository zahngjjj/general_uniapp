<template>
	<view class="charts-box">
	  <qiun-data-charts 
		type="mix"
		:opts="opts"
		:chartData="chartData"
	  />
	</view>
  </template>
  
  <script>
  export default {
	data() {
	  return {
		chartData: {},
		//您可以通过修改 config-ucharts.js 文件中下标为 ['mix'] 的节点来配置全局默认参数，如都是默认参数，此处可以不传 opts 。实际应用过程中 opts 只需传入与全局默认参数中不一致的【某一个属性】即可实现同类型的图表显示不同的样式，达到页面简洁的需求。
		opts: {
		  color: ["#1890FF","#91CB74","#FAC858","#EE6666","#73C0DE","#3CA272","#FC8452","#9A60B4","#ea7ccc"],
		  padding: [15,15,0,15],
		  enableScroll: false,
		  legend: {},
		  xAxis: {
			disableGrid: true,
		  },
		  yAxis: {
			disabled: false,
			disableGrid: false,
			splitNumber: 5,
			gridType: "dash",
			dashLength: 4,
			gridColor: "#CCCCCC",
			padding: 10,
			showTitle: true,
			data: [
			  {
				position: "left",
				title: "数量(万箱)"
			  },
			  {
				position: "right",
				min: 0,
				max: 200,
				title: "比例%",
				textAlign: "left"
			  },
			]
		  },
		  extra: {
			mix: {
			  column: {
				width: 20
			  }
			}
		  }
		}
	  };
	},
	onReady() {
	  this.getServerData();
	},
	methods: {
	  getServerData() {
		//模拟从服务器获取数据时的延时
		setTimeout(() => {
		  //模拟服务器返回数据，如果数据格式和标准格式不同，需自行按下面的格式拼接
		  let res = {
			  categories: ["1月","2月","3月","4月","5月","6月","7月","8月","9月","10月","11月","12月"],
			  series: [
				// {
				//   name: "曲面",
				//   type: "area",
				//   style: "curve",
				//   data: [70,50,85,130,64,88,70,50,85,130,64,88],
				//   disableLegend: true
				// },
				{
				  name: "目标",
				  index: 1,
				  type: "column",
				  labelShow: false,
				  data: [40,30,55,110,24,58,70,50,85,130,64,88]
				},
				{
				  name: "实际",
				  index: 1,
				  type: "column",
				  labelShow: false,
				  data: [50,20,75,60,34,38,50,20,75,60,34,38]
				},
				{
				  name: "完成比例",
				  type: "line",
				  style: "curve",
				  labelShow: false,
				  color: "#ffcf3a",
				  disableLegend: true,
				  data: [70,50,85,130,64,88,70,50,85,130,64,88]
				},
			  ]
			};
		  this.chartData = JSON.parse(JSON.stringify(res));
		}, 500);
	  },
	}
  };
  </script>
  
  <style scoped>
	/* 请根据实际需求修改父元素尺寸，组件自动识别宽高 */
	.charts-box {
	  width: 100%;
	  height: 300px;
	}
  </style>