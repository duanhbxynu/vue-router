<template>
	<home>
		<p>Welcome home</p>
		<div id="home">
			{{msg}}
			<button v-on:click="setMsg()">设置值</button>
			<ul>
				<li v-for="item in list">{{item}}</li>
			</ul>
			<button @click="setList()">设置list的值</button>
		</div>
		<div id="name">
			<ul>
				<li v-for="item in datas">
					<p>时间：{{item.addtime}}</p>
					<p>积分：{{item.integral}}</p>
					<p>原因：{{item.source}}</p>
				</li>
			</ul>
		</div>
		<button v-if="remove" @click="lookmore()">查看更多</button>
	</home>
</template>
<script>
	import Vue from 'vue'
	import Home from '../../layouts/Main.vue'

	var page = 2;
	export default {
		data() {
			return {
				msg: "123456789",
				list: ["2019"],
				datas: [],
				remove: true
			}
		},
		mounted() {
			this.setList()
		},
		components: {
			Home
		},
		methods: {
			setMsg: function() {
				this.msg = "我是设置后的msg值"
			},
			setList: function() {
				this.list = [];
				for(var i = 0; i < 10; i++) {
					this.list.push(i);
				}
			},
			lookmore: function() { //分页，查看更多
				var that = this;
				that.$http.post("http://m.5g.me/jfscmx/", {
					page: page
				}, {
					emulateJSON: true
				}).then(function(res) {
					var data = res.body;
					console.log(data)
					if(data == 'null' || data == "") {
						//移除查看更多按钮
						that.remove = false;
					} else {
						page++;
						for(var i = 0; i < data.length; i++) {
							that.datas.push(data[i]);
						}
					}
				})
			},

		}
	}
</script>
<style scoped>
	#home ul li {
		font-size: 12px;
	}
	
	#home button {
		font-size: 24px;
	}
	
	#name ul li {
		list-style: none;
		background: #cccccc;
		margin-bottom: 10px;
		padding: 5px 0;
	}
	
	#name ul li p {
		font-size: 12px;
		padding-left: 20px;
	}
</style>