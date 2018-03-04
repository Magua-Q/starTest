<template>
	<div class="rating">
		<ul class="list">
			<li v-for="star in maxStars" 
			:class="{'active':star <=stars}"
			@click="rate(star)"
			class = "star">
			<icon :name="star <= stars ? 'star':'star-o'"></icon></li>
			<!-- <li class="star active"><icon name="star"></icon></li>
			<li class="star active"><icon name="star"></icon></li>
			<li class="star"><icon name="star-o"></icon></li>
			<li class="star"><icon name="star-o"></icon></li> -->
		</ul>
		<span>{{stars}} of {{maxStars}}</span>
	</div>
</template>

<script >
	import "vue-awesome/icons/star"
	import "vue-awesome/icons/star-o"
	import Icon from "vue-awesome/components/Icon.vue"
	export default {
		components: {Icon},
		data(){
			return {
				stars:2,
				maxStars:6
			}
		},
		methods:{
			rate(star){
				this.stars = this.stars === star ?star-1:star
			}
		}
	}
</script>

<style lang="scss" scoped>
	.rating {
		border: 1px solid blank;
		font-size: 16px;
		color: #a7a8a8;
	}
	.list {
		list-style: none;
		padding: 0;
		margin: 0 0 5px 0;
	}
	.list:hover .star {
		color: #f3d23e
	}
	.star {
		display: inline-block;
		cursor: pointer;
	}
	.star:hover ~ .star:not(.active) {
		color: inherit;
	}
	.active {
		color: #f3d23e;
	}
</style>
