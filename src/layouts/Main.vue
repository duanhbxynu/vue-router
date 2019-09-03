<template>
  <div class="container">
    <ul v-if="headershow">
      <li class="tab">
        <v-link href="/">Home</v-link>
        <v-link href="/about">About</v-link>
        <v-link href="/say">Say</v-link>
        <v-link href="/login">登录</v-link>
        <v-link href="/register">注册</v-link>
      </li>
    </ul>

    <slot></slot>
  </div>
</template>

<script>
	import route from 'route'
  import VLink from '../components/VLink.vue'

  export default {
  	data(){
  		return {
  			headershow:true
  		}
  	},
    components: {
      VLink
    },
    mounted(){
    	console.log(window.location.pathname)
    	if(window.location.pathname === "/shop"){
    			this.headershow = false;
    		}else{
    			this.headershow = true;
    		}
    }
  }
</script>

<style scoped>
  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 15px 30px;
    background: #f9f7f5;
  }
  .tab{
  	list-style: none;
  	background: #ffffff;  	
  	text-align: center;
  }
  .tab a{
    display: inline-block;
    padding: 10px;
    text-decoration: none;
  }
  .tab a:hover{
  	background: aqua;
  }
  .tab a.active{
  	background: aqua;
  }
</style>
