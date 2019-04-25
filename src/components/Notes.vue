<template>
		<!-- note list -->
	<div class="notes">
		<div class="note" v-for="(note, index) in notes" :key="index">
			<div class="note-header">
				<p>{{ note.title }}</p>
				<p style="cursor: pointer;" @click="removeNote(index)">x</p>
		  </div>
			<div class="note-body">
				<p>{{ note.descr }}</p>
				<span>{{ note.date }}</span>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		notes: {
			type: Array,
			required: true
		}
	},
	methods: {
		removeNote (index){
			console.log(`Note id - ${index} removed`);
			this.$emit('remove', index)
		}
	}
}
</script>

<style lang="scss" scoped>
	.notes{
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
		padding: 40px 0;
	}
	.note{
		width: 48%;
		padding: 18px 20px;
		margin-bottom: 20px;
		background-color: #ffffff;
	}
	.note-body{
		p{
			margin: 20px 0; 
		}
		span{
			font-size: 14px;
			color: #999999;
		}
	}
	.note-header{
		display: flex;
		align-items: center;
		justify-content: space-between;
		p{
			color: #5524a5;
			font-size: 22px;
		}
	}

</style>
