<template>
	<div class="ok">
		<div class="layout">
			<transition-group :duration="{ enter: 500, leave: 100 }" name="items" tag="div" class="tourlist" v-if = "showSearch">
				<tour-item 
					:item = "item"
					v-for = "(item,index) in filterCity"
					:key = "item.id"
					:data-index = "item.id"
				>
				</tour-item>
			</transition-group>

			<div v-else>
				<p>景点暂无</p>
			</div>
		</div>
		
		<!-- <transition-group name="fade" tag="div" class="tourlist tourlist2">
			<tour-item2 
				:item = "sonItem"
				v-for = "(sonItem,index) in filterCity2"
				:key =" index"
				:upId = "item.id"
			>
			</tour-item2>
		</transition-group> -->
	</div>
</template>

<script>
	import TourItem from '~/components/touritem.vue'
	import TourItem2 from '~/components/touritem2.vue'

	export default{
		components:{
			TourItem,
			TourItem2
		},
		created(){
			this.getItem()
		},
		data(){
			return{
				item:{},
				hideData:true,
				activeName2:0
				
			}
		},
		methods:{
			getItem(){
				this.item = this.$store.state.city
			},
			change(xz){
				this.$store.commit('changeShow',xz)
			}
		},
		watch:{
			filterCity(){
			},
			filterCity2(){}
		},
		computed:{
			txt(){
				return this.$route.query.txt
			},
			showSearch(){
				return this.$store.state.showSearch
			},
			filterCity(){
				let txt = this.$route.query.txt || ''
				if(txt === ''){
					this.change(false)
					return
				}else{
					let txt = this.txt
					let province = this.$store.state.city
					let len = province.length || 0
					let arr = []
					for(let i=0;i<len;i++){
						if(province[i].name.indexOf(txt)>=0){
							arr.push(province[i])
						}
					}
					if(arr.length === 0){
						this.change(false)
					}else{
						this.change(true)
					}
					return arr
				}
			},
			// filterCity2(){
			// 	let txt = this.$route.query.txt || ''
			// 	if(txt === ''){
			// 		this.change(false)
			// 		return
			// 	}else{
			// 		let txt = this.txt
			// 		let province = this.$store.state.city
			// 		let len = province.length || 0
			// 		let arr2 = []

			// 		province.forEach(function(item,index,array){
			// 			console.log(item)
			// 			// item[index].forEach(function(item2,index2){
			// 			// 	// console.log(item2+',' +index2)
			// 			// 	console.log(1)
			// 			// })
			// 		})


			// 		// for(let x=0;x<len;x++){
			// 		// 	// console.log(province[i])
			// 		// 	let len2 = province[x].child.length || 0

			// 		// 	console.log(len2)
			// 		// 	for(let y = 0;y< len2;y++){
			// 		// 		let len3 = province[x].child[y].sonchild.length || 0
			// 		// 		for(let z = 0;z < len3;z++){
			// 		// 			// if(province[x].child[y].sonchild[z].name.indexOf(txt)>=0){
			// 		// 			// 	arr2.push(province[x].child[y].sonchild[z])
			// 		// 			// }
			// 		// 			// arr2.push(province[x].child[y].sonchild[z].name)
			// 		// 		}
			// 		// 	}
			// 		// }
			// 		// console.log(arr2)

			// 		// if(arr2.length === 0){
			// 		// 	this.change(false)
			// 		// }else{
			// 		// 	this.change(true)
			// 		// }
			// 		// return arr2
			// 	}
			// }
		}
	}
</script>

<style scoped>
	.ok{
		margin-top: 150px
	}

	.tourlist{
		float: none;
		width: 100%;
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		grid-gap: 20px;
		padding: 0 !important;
	}

	.tourlist2{
		display: block;
		width: 100%
	}

</style>