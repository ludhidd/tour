<template>
	<div class="touritem">
		<nuxt-link :to="{ name:'list',query: {id: item.id}}">
			<img :src="`/${item.img}`">
			<p>{{item.name}}</p>
		</nuxt-link>
	</div>
</template>

<script>
	export default{
		props:{
			item:{
				type:Object,
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
		padding: 10px;
		background: white;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		position: relative;
		border-radius: 5px;
		overflow:hidden;
		transition: all 1s ease;
		position: relative;
	}

	.touritem:hover{
		transform: scale(1.05);
	}

	.touritem:hover:before{
		width: 100%;
		height: 100%
	}

	img{max-width: 100%;transition: all .5s ease}
	p{
		text-align: center;
		font-size: 16px;
		color:#333;
		font-family: cursive;
	}
	.touritem a:hover p{
		color: #409EFF;
	}
</style>