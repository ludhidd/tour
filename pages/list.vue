<template>
	<div class="list">
		<div class="layout">
			<!-- 手风琴排版 -->
			<!-- <el-collapse v-model="activeName" @change="handleChange" accordion>
				<el-collapse-item :name="index" v-for="(sonItem,index) in item.child" :title="sonItem.sonName">
					<div class="listname">asdd</div>
				</el-collapse-item>
			</el-collapse> -->

			<div class="info">
				{{item.info}}
			</div>

			<div class="list-top">
				<el-tabs v-model="activeName2"  type="border-card" @tab-click="handleClick">

					<el-tab-pane v-for = "(sonItem,index) in item.child" :label="sonItem.name" :name="sonItem.id">

						<div v-if = "item.child[activeName2].sonchild === undefined || item.child[activeName2].sonchild.length === 0 ">暂无景点</div>
						
						<transition-group name="fade" tag="div" class="tourlist" v-else>
							<tour-item2 
								:item = "sonItem"
								v-for = "(sonItem,index) in item.child[activeName2].sonchild"
								:key =" index "
								:upId = "item.id"
								:activeId = 'activeName2'
							>
							</tour-item2>
						</transition-group>
					</el-tab-pane>
				</el-tabs>
			</div>
		</div>

	</div>
	
</template>
<script type="text/javascript">
	import TourBanner from '~/components/tourBanner.vue'
	import TourItem2 from '~/components/touritem2.vue'
	export default{
		components: {
			TourBanner,
			TourItem2
		},
		data(){
			return{
				item:{},
				activeName:'1',
				activeName2: '0'
			}
		},
		methods:{
			getItem(){
				this.item = this.$store.state.city[this.$route.query.id]
				// this.item = this.$store.state.selectItem
			},
			handleClick(){

			}
		},
		created(){
			this.getItem()
		}
	}
</script>

<style>
	.list{margin-bottom: 20px;padding-bottom: 40px}
	.el-collapse-item__header{
		padding: 0 20px
	}
	.el-collapse-item__content{
		padding: 0 20px;
		padding-bottom: 10px;
	}
</style>

<style scoped>
	.list{
		margin-top: 100px
	}
	.info{
		font-size: 16px;
		line-height: 32px;
		color: #333;
		margin-bottom: 20px;
		text-align: justify;
	}
	.tourlist{
	    width: 100%;
	    display: block;
	}
</style>