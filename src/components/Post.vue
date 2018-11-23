<template>
	<div class="item">
		<div class="img">
			<img v-bind:src="item.img" v-bind:alt="item.title" />
			<!-- <img src="../assets/images/rose-2417334_640.jpg" v-bind:alt="item.title" /> -->
		</div>
		<div class="info">
			<p class="title">{{item.title}}</p>
			<div class="tags"><a href="javascript:void(0)">#beauty</a> <a href="javascript:void(0)">#glass</a> <a href="javascript:void(0)">#mint</a> <a href="javascript:void(0)">#green</a> <a href="javascript:void(0)">#white</a> <a href="javascript:void(0)">#health</a></div>
			<div class="addit">
				<a href="javascript:void(0)" class="looks">
					<img src="../assets/images/if_eye_118676 (1).png" alt="looks" />
					{{item.addit.looks}}
				</a>
				<a href="javascript:void(0)" v-on:click="likeCounter" class="likes">
					<img src="../assets/images/if_heart-01_186400.png" alt="likes" />
					{{counter}}
				</a>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Post',
	data: function() {
		return {
			counter: (localStorage.getItem('liked' + this.item.id)) ? JSON.parse(localStorage.getItem('liked' + this.item.id)).likes : this.item.addit.likes
		}
	},
	props: {
		item: Object
	},
	methods: {
		likeCounter: function(event) {
			if(event) {
				var target = localStorage.getItem('liked' + this.item.id);

				if(target) {
					this.counter -= 1;
					localStorage.removeItem('liked' + this.item.id);
				} else {
					this.counter += 1;
					localStorage.setItem('liked' + this.item.id, JSON.stringify({
						id: this.item.id,
						liked: true,
						likes: this.counter
					}));
				}
			}
		}
	}
}
</script>

<style scoped>
.item {
	background-color: #fff;
}
.item:hover {
	box-shadow: 0px 0px 10px #fff;
}
.item .img {
	overflow: hidden;
	height: 170px;
}
.item .img img {
	width: 100%;
	-moz-transition: all 1s ease-out;
	-o-transition: all 1s ease-out;
	-webkit-transition: all 1s ease-out;
}
.item .img img:hover {
	-webkit-transform: scale(1.13);
	-moz-transform: scale(1.13);
	-o-transform: scale(1.13);
}
.item .info {
	padding: 14px 18px;
}
.item .info .title {
	color: #000;
	font-size: 16px;
	letter-spacing: 0.8px;
	margin-bottom: 15px;
}
.item .info .tags {
	margin-bottom: 15px;
}
.item .info .tags a {
	color: #49bbf0;
	font-size: 12px;
	letter-spacing: 0.6px;
	text-decoration: none;
    display: inline-block;
    margin-right: 4px;
}
.item .info .tags a:hover {
	color: #37a1d2;
}
.item .info .addit a {
	color: #515151;
	font-size: 12px;
	letter-spacing: 0.6px;
	text-decoration: none;
	margin-right: 15px;
}
.item .info .addit a:hover {
	color: #000;
}
.item .info .addit a img {
	height: 10px;
}
</style>
