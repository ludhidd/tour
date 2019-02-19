<template>
	<div class="banner" >
		<!-- <img :src="`/${img}.jpg`">
		<h3 class="name" v-if="name">{{name}}</h3> -->

		<el-carousel :interval="5000" arrow="always" width="100%">
			<el-carousel-item v-for="item in img" :key="item">
				<img :src="item">
			</el-carousel-item>
		</el-carousel>

	</div>
</template>

<script>
	export default{
		props:{
			img:{
				type:Array,
				required:true
			}
		},
		created(){
			// console.log(this.img)
		}
	}
</script>


<style scoped>
	
	.banner{
		width: 100%;
		/*max-width: 1280px;*/
		margin: 0 auto;
		/*height: 300px;*/
		overflow: hidden;
		position: relative;
		margin-bottom: 20px;
		z-index: 0;
		/*padding-bottom: 15.625%*/
	}
	/*.banner:before{
		content: "";
	    z-index: 10;
	    position: absolute;
	    top: 0;
	    right: 0;
	    bottom: 0;
	    left: 0;
	    background: radial-gradient(ellipse at center,transparent 0,transparent 36%,rgba(0,0,0,.65) 100%);
	    filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="rgba(0, 0, 0, 0)",endColorstr="rgba(166, 0, 0, 0)",GradientType=1);
	    opacity: .6;
	}*/

	.banner img{
		position: absolute;
		top: 50%;
		left:0;
		transform: translate(0,-50%);
		max-width: 100%;
		width:100%;
	}
	.name{
		position: absolute;
		left: 8%;
		bottom: 20px;
		font-size: 30px;
		color:#fff;
		font-family: cursive;
		z-index: 100
	}
</style>