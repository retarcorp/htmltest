<template>
	<div id="items">
		<div v-for="item in items" v-bind:key="item.id">
			<Post v-bind:item="item" />
		</div>
	</div>
</template>

<script>
import Post from '../components/Post.vue'

export default {
	name: 'Posts',
	components: {
		Post
	},
	props: {
		items: Array
	}
}
</script>

<style scoped>
#items {
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	grid-column-gap: 60px;
	grid-row-gap: 50px;
}
@media (max-width: 768px) {
	#items {
		grid-template-columns: repeat(2, 1fr);
		grid-column-gap: 30px;
		grid-row-gap: 30px;
	}
}
@media (max-width: 400px) {
	#items {
		grid-template-columns: repeat(1, 1fr);
		grid-column-gap: 20px;
		grid-row-gap: 20px;
	}
}
</style>
