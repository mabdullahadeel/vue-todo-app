<template>
	<header><h1 class="heading">{{ title }}</h1></header>
</template>


<script>
export default {
	name: "Header",
	props: {
		title: String,
	},
};
</script>

<style scoped>
header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 20px;
	height: 30px;
	padding: 30px 0px;
	}
.heading{
	font-size: 30px;
	color: rgb(59, 211, 135);
}
</style>