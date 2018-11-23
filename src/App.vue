<template>
	<div id="app">
		<Header />
		<Content v-bind:items="items" />
	</div>
</template>

<script>
import axios from 'axios'
import Header from './components/Header.vue'
import Content from './components/Content.vue'

export default {
	name: 'app',
	components: {
		Header,
		Content
	},
	created() {
		this.fetchData();	
	},
	data: function() {
		return {
			items: []
		}
	},
	methods: {
		fetchData() {
			axios.get('data.json').then(response => {
				this.items = response.data.items;
				console.log(this.items);
			}).catch(function(error) {
				alert(error);
			});
		}
	}
}
</script>

<style>
@font-face {
	font-family: StolzlBook;
	src: url('./assets/fonts/Stolzl-Book.otf');
}
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
#app {
	font-family: StolzlBook;
	background: linear-gradient( rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.8) ), url(./assets/images/cyprus-3184019_1920.jpg) no-repeat top center;
	background-size: cover;
	background-attachment: fixed;
}
::-webkit-scrollbar {
	width: 10px;
}
::-webkit-scrollbar-track {
	background: #eaeaea; 
}
::-webkit-scrollbar-thumb {
	background: #a3c755; 
	border-radius: 5px;
}
::-webkit-scrollbar-thumb:hover {
	background: #3d6f2f; 
}
</style>
