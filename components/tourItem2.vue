<template>
	<div class="touritem">
		<nuxt-link :to="{ name:'desc',query: {id: item.id,upId:upId,activeId:activeId}}" class="fix">
			<div class="pic">
				<img :src="`/${item.img}`">
			</div>
			<div class="word">
				<h3>{{item.name}}</h3>
				<p>{{item.info}}</p>
			</div>
		</nuxt-link>
	</div>
</template>

<script>
	export default{
		props:{
			item:{
				type:Object,
				required:true
			},
			upId:{
				type:String,
				required:true
			},
			activeId:{
				type:String,
				required:true
			}
		},
		methods:{
			getItem(item){
				// this.$store.commit({
				// 	type: 'getItem',
				// 	item: item
				// })
			}
		}
	}
</script>

<style scoped>
	.touritem{
		border-radius: 5px;
		padding:20px 10px;
		background: white;
		position: relative;
		border-radius: 5px;
		overflow:hidden;
		transition: all 1s ease;
		position: relative;
		box-shadow: 0 0 6px rgba(0,0,0,.6);
		margin-bottom: 10px
	}

	.pic{
		float: left;
		width: 20%
	}
	.word{
		float: left;
		width: 75%;
		margin-left: 5%;
		text-align: left;
	}
	img{max-width: 100%;transition: all .5s ease}
	h3{
		font-size: 20px;
		color:#333;
		font-family: cursive;
		font-weight: bold;
		margin-bottom: 15px
	}
	p{
		font-size: 14px;
		color:#666;
		font-family: cursive;
	}
	.touritem a:hover p{
		color: #409EFF;
	}
</style>