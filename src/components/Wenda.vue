<template>
	<div>
		<van-nav-bar fixed title="问答" left-text="返回" left-arrow @click-left="onClickLeft" />
		<ul>
			<li>
				<h4>宝宝晒太阳有哪些注意事项？？</h4>
				<span>
					<img src="../assets/96.jpg"/><em>小糖果</em>
				</span>
				<p>给宝宝晒太阳好处多多，能够帮助孩子合成维生素D，这个东西促进钙质吸收可是大有好处。这就是晒太阳长个子的由来！除此之外还能促进宝宝的新陈代谢增强机体抗病能力呢！</p>
			    <i>166个赞-11个评论</i>
			</li>
			<li>
				<h4>一岁一下的宝宝不能喝水么？？</h4>
				<span>
					<img src="../assets/96.jpg"><em>茜茜公主</em>
				</span>
				<p>给宝宝晒太阳好处多多，能够帮助孩子合成维生素D，这个东西促进钙质吸收可是大有好处。这就是晒太阳长个子的由来！除此之外还能促进宝宝的新陈代谢增强机体抗病能力呢！</p>
			     <i>99个赞-10个评论</i>
			</li>
		</ul></div>
</template>
<script>
	export default {
		methods: {
			onClickLeft() {
				this.$router.go(-1)
			},	
		}
	}
</script>
<style scoped>
i,span,h1,ul li{margin:0;padding:0}
li{list-style:none;}
div ul li p{margin:0 0 10px 0}
div ul{margin-top:47px;font-size:14px}
div ul li span{display:block;width:120px;height:50px;margin:10px 0}
div ul li img{display:block;border:0;width:50px;height:50px;float:left;border-radius:50%;margin-right:8px}
div ul li em{font-style:normal;margin-top:15px;float:left}
div ul li{margin:0 0 20px 0;height: 240px;line-height: 20px;background-color: rgba(242, 242, 242, 1);
border: 1px solid rgba(255, 255, 255, 0);padding:20px 20px}


</style>
