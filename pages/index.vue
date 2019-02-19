<template>
	<section class="main">

		<tour-banner :img = 'imgList'></tour-banner>
		<div class="layout fix">
			<tour-left @selectArea = "selectArea"></tour-left>
			<transition-group :duration="{ enter: 1000, leave: 0 }" name="items" tag="div" class="tourlist">
				<tour-item 
					:item = "item"
					v-for = "(item,index) in filterCity"
					:key = "item.id"
                    :data-index = "item.id"
				>
				</tour-item>
			</transition-group>
		</div>
	</section>
</template>

<script>
	import axios from 'axios'
	import TourBanner from '~/components/tourBanner.vue'
	import TourLeft from '~/components/tourleft.vue'
	import TourItem from '~/components/touritem.vue'

export default {
	components: {
		TourLeft,
		TourItem,
		TourBanner
	},
	data(){
		return{
			citys:[],
			param:'全部',
			imgList:this.$store.state.bannerImg
		}
	},
	created(){
	},
	methods:{
		selectArea(param){
			this.param = param
		}
	},
	computed:{
		filterCity(param){
			if(this.param === '全部'){
				return this.$store.state.city
			}
			return this.$store.state.city.filter(item=> this.param === item.area)
		}
	}
}
</script>

<style>
.main{
	margin: 85px 0 20px;
	padding-bottom: 40px;
}

.tourlist{
	float: right;
	width: 88%;
	display: grid;
	grid-template-columns: repeat(4, 1fr);
	grid-gap: 20px;
	padding: 0 !important;
}
</style>
