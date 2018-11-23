<template>
	<header>
		<div class="title">Test Project</div>
	</header>
</template>

<script>
export default {
	name: 'Header',
	props: {
	}
}
</script>

<style scoped>
header {
	padding: 18px 52px;
	position: fixed;
	top: 0;
	right: 0;
	left: 0;
	background-color: #eaeaea;
	border-top: 4px solid #a3c755;
}
.title {
	color: #3d6f2f;
	font-size: 24px;
	font-weight: 400;
	letter-spacing: 1.2px;
}
</style>
