<template>
	<div class="content">
		<h1>World’s most <span>amazing</span> test tiles</h1>
		<Posts v-bind:items="items" />
	</div>
</template>

<script>
import Posts from '../components/Posts.vue'

export default {
	name: 'Content',
	components: {
		Posts
	},
	props: {
		items: Array
	}
}
</script>

<style scoped>
.content {
	width: 900px;
	margin: 0 auto;
	padding: 100px 0;
}
h1 {
	color: #eaeaea;
	font-size: 48px;
	font-weight: 400;
	letter-spacing: 2.4px;
	text-align: center;
	margin-bottom: 50px;
}
h1 span {
	color: #a3c755;
}
@media (max-width: 768px) {
	.content {
		width: 100%;
		padding-left: 10px;
		padding-right: 10px;
	}
}
</style>
