<template>
	<login-to>
		<p>login.vue</p>
		<label for="name">号码：</label>
		<input type="text" placeholder="请输入用户名" v-focus v-model.trim="message" v-on:change="change()"/>
		<span  v-if="tip1">*请输入正确的手机号</span>
		<br /><br />
		<label for="psw">密码：</label>
		<input type="password" placeholder="请输入密码" v-model.trim = "message2" v-on:change="change()"/>
		<span v-if="tip2">*请输入6--16位密码</span>
		<br />
		<br />
		<button v-on:click="login()">登录</button>
		<button>
			<v-link href="/register">去注册</v-link>
		</button>
		<br />
		<br />
		<button>
			<v-link href="/good">点击有惊喜</v-link>			
		</button>
		
		<button>
			<v-link href="/shop">shop</v-link>
		</button>
		
	</login-to>
</template>

<script>
	import Vue from 'vue'
	import loginTo from '../../layouts/Main.vue'
	import VLink from '../../components/VLink.vue'
	
	//自定义指令
	Vue.directive('focus',{
		inserted:function(e){
			e.focus();
		}
	});
	
	export default {
		components: {
			loginTo,
			VLink
		},
		data(){
			return {
				message:"",
				message2:"",
				tip1:false,
				tip2:false
			}
		},
		methods:{
			change:function(){
				var that = this;
				var reg = /^1[3456789]\d{9}$/;
				var reg2 = /^[a-zA-Z0-9_-]{6,16}$/;
				var bool = reg.test(that.message);
				var bool2 = reg2.test(that.message2);
				if (!bool){
					this.tip1 = true;
				} else if (!bool2){
					this.tip2 = true
				}else {
					this.tip1 = false;
					this.tip2 = false
				}
			},
			login:function(){
				this.change()
				
			}
			
			
		}
	}
</script>
<style scoped="">
	span{
		color: red;
	}
</style>