<template>
	<div id="home">
		<home-banner></home-banner>
		<section class="navBox">
			<div class="mainNav"  v-for="(item,index) in navlists">
				<img :src = "item.imgurl" />
				<p>{{ item.navtitle }}</p>
			</div>
		</section>
		<section class="hotBox">
			<p>热门咨询</p>
			<div class="hotConsult">
				<div class="consultImgbox">
					<img src="../../static/images/talkdetail.jpg">
				</div>
				<div class="hotConsultbox">
					<div class="hotTitle">为什么母亲唱儿歌给婴儿歌</div>
					<div class="hotContent">母亲对她的婴儿唱歌是一种怎么样的是一种怎么样的是一种怎么样的</div>
				</div>
			</div>
			<div class="hotConsult">
				<div class="consultImgbox">
					<img src="../../static/images/talkdetail.jpg">
				</div>
				<div class="hotConsultbox">
					<div class="hotTitle">为什么母亲唱儿歌给婴儿歌</div>
					<div class="hotContent">母亲对她的婴儿唱歌是一种怎么样的是一种怎么样的是一种怎么样的</div>
				</div>
			</div>
		</section>
		<foot-guide></foot-guide>
	</div>
	
</template>
<script>
	import footGuide from '../components/footer'
	import homeBanner from '../components/banner'
	export default {
		data(){
			return {
				navlists:[
					{
						imgurl:'./static/images/wenzhen.png',
						navtitle:'我的诊室'
					},
					{
						imgurl:'./static/images/xuexi.png',
						navtitle:'学习'
					},
					{
						imgurl:'./static/images/zhaotonghang.png',
						navtitle:'找同行'
					},
					{
						imgurl:'./static/images/chufang.png',
						navtitle:'电子处方'
					},
					{
						imgurl:'./static/images/bingli.png',
						navtitle:'发布病例'
					},
					{
						imgurl:'./static/images/shuoshuo.png',
						navtitle:'发布说说'
					}
				]
			}
		},
		components:{
			footGuide,
			homeBanner
		},
		beforeMount(){
			var formData = new FormData();
			this.$http.post('/doctor/hot/api/getHotList.do',formData).then(response => {
				    console.log(response.body);

				  }, response => {
				    // error callback 
				    console.log('error');
			  });
		}
	}
</script>
<style lang='scss' scoped>
	#home{
		display: box;
		padding-bottom: 1rem;
		.navBox{
			background:#ffffff;
			display: flex;
			flex-direction:row;
			flex-wrap: wrap;
			.mainNav{
				width: 2.5rem;
				img{
					width: 1rem;
					height: 1rem;
					margin: 0 auto;
				};
				p{
					width: 100%;
					height: 0.6rem;
					line-height: 0.6rem;
					font-size: 0.3rem;

				}
			}

		}
		.hotBox{
			width: 100%;
			display: box;
			box-sizing: border-box;
			padding: 0.5rem 0 0 0.4rem;
			background: white;
			p{
				width: 100%;
				font-size: 0.36rem;
				color: #333333;
				text-align: left;
			}
			.hotConsult{
				overflow:hidden;
				padding: 0.34rem 0.3rem 0.3rem 0;
				border-bottom: 1px solid #e1e1e1;
				.consultImgbox{
					width: 30%;
					height: 1.8rem;
					overflow: hidden;
					float: left;
					img{
						width: 100%;
						height: auto;
					}
				}
				.hotConsultbox{
					width: 60%;
					float: right;
					.hotTitle{
						font-size: 0.34rem;
						color: #333333;
						text-align: left;
						line-height: 0.4rem;
						text-overflow: ellipsis;
					 	display: -webkit-box;
					    	display:box;
					 	-webkit-line-clamp: 2;
					 	-webkit-box-orient: vertical;
					 	overflow:hidden;
					}
					.hotContent{
						font-size: 0.3rem;
						color:#999999;
						overflow: hidden;
						text-overflow: ellipsis;
						-o-text-overflow: ellipsis;
						white-space: nowrap;
					}
				}
			}
			
		}
	}
</style>