<template>
	<section class="footbox">
		<div class="footer home" @click="goto('/')">首页</div>
		<div class="footer consult" @click="goto('/consult')">咨询</div>
		<div class="footer message" @click="goto('/message')">消息</div>
		<div class="footer mycenter" @click="goto('/mycenter')">我</div>
	</section>
	
</template>
<script>
	export default{
		data(){
			return{
				msg: '嗷嗷'
			}
		},
		created(){

		},
		methods:{
			goto(path){
				this.$router.push(path)
			}
		}
	}
</script>
<style lang="scss" scoped>
	@import './static/css/mixin.scss';
	.footbox{
		width: 100%;
		height: 1rem;
		display: flex;
		flex-direction:row;
		background: white;
		position: fixed;
		left: 0;
		bottom: 0;
		z-index: 100;
		.footer{
			display: box;
			flex:1;
			font-size: 0.2rem;
			padding-top: 0.14rem;
			color: #999999;
		}
		.home{
			@include footerbg('../../static/images/index.png');
		}
		.consult{
			@include footerbg('../../static/images/consult.png');
		}
		.message{
			@include footerbg('../../static/images/message.png');
		}
		.mycenter{
			@include footerbg('../../static/images/me.png');
		}	
	}
	
	
</style>