<template>
	<view class="content">
		<uni-section title="通用写法" type="line"></uni-section>
		<view style="margin-top: 30rpx;">
			<luyj-select-lay :zindex="1211" :loading="loading" :value="tval" name="name" placeholder="请选择项目" :options="datalist"
				@selectitem="selectitem">
			</luyj-select-lay>
		</view>
		
		<uni-section title="禁用组件" type="line"></uni-section>
		<view  style="margin-top: 30rpx;">
			<luyj-select-lay :zindex="1111" :loading="loading" :value="tval" name="name2" placeholder="请选择项目(禁用)" :options="datalist"
				:disabled="true">
			</luyj-select-lay>
		</view>
		<uni-section title="自定义数据索引对象" type="line"></uni-section>
		<view style="margin-top: 30rpx;">
			<luyj-select-lay :loading="loading" :value="tval" name="name3" slabel="myname" svalue="myvalue" placeholder="请选择项目(自定义数据)"
				:options="datalist2" @selectitem="selectitem2">
			</luyj-select-lay>
		</view>
		<uni-section title="数据加载中" type="line"></uni-section>
		<view style="margin-top: 30rpx;">
			<luyj-select-lay :zindex="1211" :loading="true" :value="tval" name="name" placeholder="请选择项目" :options="datalist"
				@selectitem="selectitem">
			</luyj-select-lay>
		</view>
		<button style="margin: 30rpx;" @click="getDatas">重新加载数据</button>
	</view>
</template>

<script>
	import datas from '@/common/data.js'; // 数据
	var _self;
	export default {
		data() {
			return {
				loading : false,	// 数据是否加载中
				datalist: [], // 模拟数据
				datalist2: [], // 模拟自定义数据
				tval: "" // 模拟初始数据
			}
		},
		onLoad: function() {
			_self = this;
			this.getDatas();
		},
		methods: {
			/**
			 * 模拟从数据库获取数据(5s)
			 */
			getDatas: function() {
				this.loading = true;
				setTimeout(function() {
					_self.loading = false;
					_self.datalist = datas.list;
					_self.datalist2 = datas.mylist;
					_self.tval = "value2";
				}, 5000);
			},
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
</style>
