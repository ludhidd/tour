<template>
	<div class="desc">
		<div class="layout">
			<h3>{{sonitem.name}}</h3>
			<p>{{sonitem.info}}</p>
			<img :src="sonitem.img">
		</div>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				sonitem:{}
			}
		},
		methods:{
			getSonItem(){
				this.sonitem = this.$store.state.city[this.$route.query.upId].child[this.$route.query.activeId].sonchild[this.$route.query.id]
			}
		},
		created(){
			this.getSonItem()
		}
	}
</script>

<style scoped>
	.desc{
		margin-top: 200px
	}
</style>