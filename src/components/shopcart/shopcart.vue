<template>
	<div class="shopcart">
		<div class="content">
			<div class="content-left">
				<div class="logo-wrapper">
					<div class="logo" :class="{'highlight':totalCount>0}">
						<i class="icon-shopping_cart"></i>
					</div>
					<div class="num">{{totalCount}}</div>
				</div>
				<div class="price">￥{{totalPrice}}</div>
				<div class="desc">另需配送费￥{{deliveryPrice}}元</div>
			</div>
			<div class="content-right">
				<div class="pay">￥{{minPrice}}起送</div>
			</div>
		</div>
	</div>
</template>

<script type="text/ecmascript-6">
	export default{
		props:{
			selectFoods:{
				type:Array,
				default(){
					return [
						{
							price:10,
							count:1
						}
					]
				}
			},
			deliveryPrice:{
				type:Number,
				default:0
			},
			minPrice:{
				type:Number,
				default:0
			}
		},
		computed:{
			totalPrice(){
				let total=0;
				this.selectFoods.forEach((food) => {
					total += food.price*food.count;
				})
				return total;
			},
			totalCount(){
				let count=0;
				this.selectFoods.forEach((food)=>{
					count+=food.count;
				})
				return count;
			}
		}
	}
</script>

<style lang="stylus" rel="stylesheet/stylus">
	.shopcart
		position fixed
		left 0
		bottom 0
		z-index 50
		width 100%
		height 48px
		.content
			display flex
			background #141d27
			font-size 0
			color rgba(255,255,255,.4)
			.content-left
				flex 1
				.logo-wrapper
					display inline-block
					vertical-align top
					position relative
					top -10px
					margin 0 12px
					padding 6px
					width 56px
					height 56px
					box-sizing border-box
					border-radius 50%
					background #141d27
					.logo
						width 100%
						height 100%
						border-radius 50%
						text-align center
						background rgba(255,255,255,.1)
						&.highlight
							background rgb(0,160,220)
							.icon-shopping_cart
								color #fff
						.icon-shopping_cart
							line-height 44px
							font-size 24px
					.num
						position absolute
						top 0
						right 0
						width 24px
						height 16px
						line-height 16px
						text-align center
						border-radius 16px
						font-size 9px
						font-weight 700
						color #fff
						background rgb(240,20,20)
						box-shadow 0 4px 8px 0 rbga(0,0,0,.4)
				.price
					display inline-block
					vertical-align top
					margin-top 12px
					padding-right 12px
					line-height 24px
					box-sizing border-box
					border-right 1px solid rgba(255,255,255,.1)
					font-size 16px
					font-weight 700
				.desc
					display inline-block
					vertical-align top
					margin 12px 0 0 12px
					line-height 24px
					font-size 10px
			.content-right
				flex 0 0 105px
				width 105px
				.pay
					height 48px
					line-height 48px
					text-align center
					font-size 12px
					font-weight 700
					background rgba(255,255,255,.1)
</style>