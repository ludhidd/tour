<template>
	<transition 
		mode="out-in"
		@before-enter="beforeEnter"
		@enter="enter"
	>
		<div class="menulist" v-show="menuListActive">
			<ul>
				<li><nuxt-link to="/">风景如画</nuxt-link></li>
				<li><nuxt-link to="/">人间美味</nuxt-link></li>
			</ul>
	
		</div>
	</transition>
</template>

<script>
	import { TweenMax, TimelineMax, Sine, Expo, Back } from 'gsap'
	export default{
		props:{
			menuListActive:{
				type:Boolean,
				default:false
			}
		},
		methods:{
			beforeEnter(el) {
		      TweenMax.set(el, {
		        opacity: 0,
		        scale: 0,
		        transformOrigin: '100% 0%'
		      })
		      TweenMax.set(el.childNodes, {
		        opacity: 0
		      })
		    },
		    enter(el, done) {
		      TweenMax.fromTo(
		        el,
		        0.2,
		        {
		          opacity: 0,
		          scale: 0
		        },
		        {
		          opacity: 1,
		          scale: 1,
		          ease: Sine.easeOut
		        }
		      )
		      TweenMax.staggerFromTo(
		        el.childNodes,
		        0.45,
		        {
		          opacity: 0
		        },
		        {
		          delay: 0.1,
		          opacity: 1,
		          ease: Sine.easeOut
		        },
		        0.04
		      )
		      done()
		    },
		}
		
	}
</script>

<style scoped>
	.menulist{
		position: absolute;
		right:0;
	}

	.menulist ul{
		padding: 15px;
		background: rgba(0,0,0,.5);
	}
	.menulist li{margin-bottom: 8px}
	.menulist li:last-child{margin-bottom: 0}
	.menulist a{
		font-size: 14px;
		color:#fff;
		line-height:24px;
	}

	.menulist a:hover{
		color:#409EFF;
	}
</style>