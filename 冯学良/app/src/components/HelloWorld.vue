<template>
	<p>
		<input type="checkbox" :value="msg" v-model="val" />
		{{ msg }}
	</p>
</template>

<script>
export default {
	name: 'HelloWorld',
	props: {
		msg: String,
	},
	data: function() {
		return {
			val:false
		};
	},
	watch: {
		val() {
			this.$emit('bl', [this.val,this.msg]);
		}
	}
};
</script>

<style scoped>
/* .hello p{
		display: inline-block;
	} */
</style>
