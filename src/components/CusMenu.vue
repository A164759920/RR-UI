<template>
	<div class='rr-menu'>
		<div class="toggle" @click="showMenu" :style="setToggleColor">+</div>
		<li class="item" v-for="(item, index) in itemList" 
		@click="item.click"
		:title="item.name" 
		:style="setItemStyle(index)">
			<div class="item-icon" :class="item.icon" ></div>
		</li>
		<!-- <li  class="item" style="--i:0">
			<a href="#"></a>
		</li>
		<li  class="item" style="--i:1">
			<a href="#"></a>
		</li>
		<li class="item"  style="--i:2">
			<a href="#"></a>
		</li>
		<li class="item" style="--i:3">
			<a href="#"></a>
		</li>
		<li class="item" style="--i:4">
			<a href="#"></a>
		</li>
		<li class="item" style="--i:5">
			<a href="#"></a>
		</li>
		<li class="item" style="--i:6">
			<a href="#"></a>
		</li>
		<li class="item" style="--i:7">
			<a href="#"></a>
		</li> -->
	</div>
</template>

<script>
export default {
	name: "CusMenu",
	props: {
		itemList: {
			type: Array,
			default: [{
				name: "default",
				icon: "null"
			}]
		},
		itemBgColor: {
			type: String,
			default: "whitesmoke"
		},
		itemColor: {
			type: String,
			default: "#757575"
		},
		toggleBgColor: {
			type: String,
			default: "#03A9F4"
		},
		toggleColor: {
			type: String,
			default: "black"
		}
	},
	data: function () {
		return {
			isShowMenu: false
		}
	},
	computed: {
		setToggleColor: function () {
			return [{
				'--toggleBgColor': this.toggleBgColor,
			}, {
				'--toggleColor': this.toggleColor
			}]
		},
	},
	methods: {
		setItemStyle: function (index) {
			return [{
				'--i': index,
			}, {
				'--itemBgColor': this.itemBgColor,
			}, {
				'--itemColor': this.itemColor
			}
			]
		},
		showMenu() {
			// classList.toggle方法可动态改变类名
			const menu = document.querySelector(".rr-menu")
			menu.classList.toggle("active")
		}
	},
	mounted: function () {
	}
}
</script>

<style scoped lang="scss">
.rr-menu {
	position: relative;
	width: 200px;
	height: 200px;
	display: flex;
	justify-content: center;
	align-items: center;

	.toggle {
		z-index: 1;
		width: 60px;
		height: 60px;
		border-radius: 50%;
		position: absolute;
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: var(--toggleBgColor);
		color: var(--toggleColor)
	}

	.toggle:hover {
		cursor: pointer;
		font-size: 20px;
		font-family: 550;
		box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
	}

	.item {
		position: absolute;
		left: 0;
		display: flex;
		justify-content: center;
		align-items: center;
		width: 40px;
		height: 40px;
		border-radius: 50%;
		background-color: var(--itemBgColor);
		list-style: none;
		transform-origin: 100px;
		transform: rotate(0deg) translateX(80px);
		transition: 0.5s;
		transition-delay: calc(0.05s * var(--i));

		.item-icon {
			color: var(--itemColor)
		}
	}
	.item:hover{
		cursor: pointer;
	}
}

.rr-menu.active {
	.item {
		transform: rotate(calc(var(--i) * 45deg));
		box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;

		.item-icon {
			transform: rotate(calc(var(--i) * -45deg));

		}


	}
}
</style>