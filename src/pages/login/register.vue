<template>
	<register-to>
		<p>填写信息注册账号</p>
		<label for="name">用户名：</label>
		<input type="text" placeholder="请输入注册用户名">
		<br /><br />
		<label for="psw">密码：</label>
		<input type="password" placeholder="请输入密码"/>
		
		<button>
			<v-link href="/login">去登录</v-link>
		</button>
		
		<br /><br />
		<button>
			<v-link href="/">返回首页</v-link>
		</button>
		<slot></slot>
	</register-to>

</template>

<script>
	import registerTo from '../../layouts/Main.vue'
	import VLink from '../../components/VLink.vue'

	export default {
		components: {
			registerTo,
			VLink
		}
	}
</script>