<template>
	<div>
		<div id="progress">
			<div id="comBox"></div>
			<span id="slider"></span>
		</div>
	</div>
</template>

<script>
	export default{
		data(){
				return{
					w:0,
				}
			},
			methods:{
				btn(){
					this.style.Position.left=250+'px'
				}
			}
	}
</script>

<style scoped="scoped">
	#progress {
		width: 600px;
		height: 20px;
		float: left;
		background-color: #ccc;
		margin: 30px auto;
		position: relative;
		border-radius: 10px;
	}
	
	#comBox {
		width: 0;
		height: 100%;
		background-color: #00BFFF;
		border-radius: 10px;
	}
	
	#slider {
		position: absolute;
		width: 30px;
		height: 30px;
		background-color: white;
		border: 5px solid #00BFFF;
		border-radius: 50%;
		top: -8px;
	}
</style>