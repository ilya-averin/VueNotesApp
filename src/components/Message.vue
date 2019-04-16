<template>
	<div class="message">
		<p>{{ message }}</p>
	</div>
</template>

<script>
export default {
	props: {
		message: {
			type: String,
			required: true
		}
	}
}
</script>

<style lang="scss" scoped>
.message{
	text-align: center;
	padding: 10px;
}

p{
	color: #ff3939;
}

</style>
