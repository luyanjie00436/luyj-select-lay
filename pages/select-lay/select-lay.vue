<template>
	<view class="content">
		<view class="item ">通用组件：</view>
		<luyj-select-lay zindex="3" :value="tval" name="name" placeholder="请选择项目" :options="datalist"
			@selectitem="selectitem">
		</luyj-select-lay>
		<view class="item ">组件状态：加载中</view>
		<luyj-select-lay zindex="3" :value="tval" name="name" placeholder="请选择项目" loading="true" :options="datalist"
			@selectitem="selectitem">
		</luyj-select-lay>
		<view class="item ">禁用组件：</view>
		<luyj-select-lay zindex="3" :value="tval" name="name2" placeholder="请选择项目(禁用)" :options="datalist"
			:disabled="true">
		</luyj-select-lay>
		<view class="item ">改变下拉框位置：</view>
		<luyj-select-lay  zindex="3" :value="tval" optionsDirection="top" name="name" placeholder="请选择项目" :options="datalist"
			@selectitem="selectitem">
		</luyj-select-lay>
		<view class="item ">自定义数据索引对象：</view>
		<luyj-select-lay zindex="3" :value="tval" name="name3" slabel="myname" svalue="myvalue" placeholder="请选择项目(自定义数据)"
			:options="datalist2" @selectitem="selectitem2">
		</luyj-select-lay>
		<!-- <view class="item ">定义为多选:</view>
		<luyj-select-lay :zindex="3" multiple :value="tval"  name="name" placeholder="请选择项目" :options="datalist"
			@selectitem="selectitem">
		</luyj-select-lay> -->
		<!-- 下一版本添加的说明 -->
		<!-- |multiple		|Boolean	|false		|	是否多选	| -->
	</view>
</template>

<script>
	import datas from './data.js'; // 数据
	var _self;
	export default {
		data() {
			return {
				datalist: [], // 模拟数据
				datalist2: [], // 模拟自定义数据
				tval: "" // 模拟初始数据
			}
		},
		onReady:function(){
			this.datalist = datas.list;
			this.datalist2 = datas.mylist;
			this.tval = "value2";
		},
		onLoad: function() {
			self = this;
			// this.getDatas();
		},
		methods: {
			/**
			 * 模拟从数据库获取数据
			 */
			// getDatas: function() {
			// 	setTimeout(function() {
			// 		_self.datalist = datas.list;
			// 		_self.datalist2 = datas.mylist;
			// 		_self.tval = "value2";
			// 	}, 3000);
			// },
			/** 切换select时执行
			 * @param {Object} index 索引
			 * @param {Object} item 值
			 */
			selectitem(index, item) {
				console.log("item=>", item, "index=>", index)
				if (index >= 0) {
					this.tval = item.value;
				} else {
					this.tval = ""
				}
			},
			/** 切换自定义索引对象时执行
			 * @param {Object} index 索引
			 * @param {Object} item 值
			 */
			selectitem2(index, item) {
				console.log("item=>", item, "index=>", index)
				if (index >= 0) {
					this.tval = item.myvalue;
				} else {
					this.tval = ""
				}
			},
		}
	}
</script>


<style>
	.content {
		width: calc(100vw -60rpx);
		padding: 30rpx;
		margin: 0 auto;
	}

	.content .item {
		margin-top: 20rpx;
		margin-bottom: 20rpx;
	}
</style>
