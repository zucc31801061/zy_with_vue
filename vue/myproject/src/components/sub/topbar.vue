<template>
	<div class="topbar">
		<div v-if="this.user==null">
			<el-avatar src="https://cube.elemecdn.com/0/88/03b0d39583f48206768a7534e55bcpng.png"></el-avatar>
			<el-col :span="12">
				<el-dropdown trigger="click">
					<span class="el-dropdown-link">
						还未登录<i class="el-icon-arrow-down el-icon--right"></i>
					</span>
					<el-dropdown-menu slot="dropdown">
						<el-dropdown-item @click.native="toregister()">注册</el-dropdown-item>
						<el-dropdown-item @click.native="tologin()">登录</el-dropdown-item>
					</el-dropdown-menu>
				</el-dropdown>
			</el-col>
		</div>
		<div class="welcome" v-if="this.user!=null">
			<span>
				你好，{{user.realname}}
			</span>
			<button @click="quit()">注销</button>
		</div>
	</div>
</template>

<script>
	export default {
		name: "topbar",
		props:{
			user: Object
		},
		methods: {
			tologin() {
				this.$router.push('/login')
			},
			toregister() {
				this.$router.push('/register')
			},
			quit(){
				localStorage.setItem("user", null);
			}
		},
		mounted(){
			console.log(this.user);
		}
	}
</script>

<style type="text/css" scoped>
	.topbar {
		position: fixed;
		width: 100%;
		left: 0;
		right: 0;
		top: 0;
		background: #a98175;
		height: 46px;
		text-align: left;
		z-index: 99;
	}

	.el-avatar {
		width: 25px;
		height: 25px;
		margin-left: 15px;
		margin-top: 10px;
	}

	.el-dropdown {
		position: fixed;
		top: 13px;
		left: 50px;
	}

	.el-dropdown span {
		color: #fff;
	}
	
	.welcome{
		line-height: 46px;
		padding-left: 20px;
	}
	
	.welcome span{
		color: #fff;
		font-size: 14px;
	}
	
	.welcome button{
		float: right;
		margin: 11px;
		background-color: #e6edf2;
		border-radius: 10px;
	}
</style>
