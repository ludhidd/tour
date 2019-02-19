<template>
	<div class="search">
		<form @submit.prevent="submit"> 
			<!-- <input type="text" ref="inputText" v-model.trim="txt">
			<input type="submit" > -->
			<input type="search" placeholder="搜索" v-model.trim="txt" ref="inputText">
			<!-- <input type="search" name=""> -->
		</form>
	</div>
</template>

<script>
	import {getStore, setStore} from '~/config/common.js'
	export default{
		data(){
			return{
				txt:''
			}
		},
		methods:{
			submit(){
				let history = JSON.parse(getStore('history'))
				history === undefined ? '' : history = []
				history.push(this.txt)
				setStore('history',JSON.stringify(history))

				this.$router.push({path: '/ok',query:{txt:this.txt}})
				this.txt = ''
				let txt = this.$refs.inputText.value;

				if(txt === undefined || txt === ''){
					return false
				}else{
					console.log(txt)
				}
			}
		}
	}
</script>

<style scoped>
	input[type=search]{
		width: 0px;
		height:30px;
		cursor:pointer;
		transition: opacity .2s,width .3s;
		padding-left:30px;
		position: relative;
		background: url(/search1.png) no-repeat -2px -2px;
		border: 1px
	}
	input[type=submit]:focus + input[type=search],
	input[type=search]:focus{
		outline: 0;
		width: 150px;
		border:1px solid #20e5a8;
		border-radius: 6px
	}
</style>