<template>
	<div class="tourleft">
		<span v-for="(select,index) in selects">
			<!-- <input type="radio" name="area" :id="select" :value="select" v-model="param" @change="selectCity">
			<label :for="select">{{select}}</label> -->
			<el-radio v-model="param" :label="index" @change="selectCity">{{select}}</el-radio>
		</span>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				param:0,
				selects:['全部','华南','华北','华中','东北','西北']
			}
		},
		methods:{
			selectCity(param){
				this.$emit('selectArea',this.selects[param])
			}
		}
	}
</script>

<style scoped>
	.tourleft{
		float: left;
		width: 10%;
		padding: 20px;
		background: #fff;
		border-radius: 4px
	}

	.tourleft span{
		font-size: 14px;
		margin-right: 10px;
		margin-bottom: 5px;
		width: 75px;
		display: inline-block;
	}
	.tourleft span:last-child{margin-bottom: 0}

	input[type="radio"] + label::before {
		content: "\a0"; /*不换行空格*/
		display: inline-block;
		vertical-align: middle;
		font-size: 18px;
		width: 10px;
		height: 10px;
		border-radius: 50%;
		border: 1px solid #1686d6;
		text-indent: .15em;
		line-height: 1; 
		position: absolute;
		left: 0;
		top: 50%;
		transform: translate(0,-50%);
	}
	input[type="radio"]:checked + label::before {
		background-color: #1686d6;
		background-clip: content-box;
		padding: 2px;
	}
	input[type="radio"] {
		position: absolute;
		clip: rect(0, 0, 0, 0);
	}
	label{
		position: relative;
	}
</style>