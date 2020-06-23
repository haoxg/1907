<template>
	<div id="app">
		<my-cert></my-cert>
   
		<my-slider></my-slider>
	</div>
</template>

<script>
	import myCert from './Transfet.vue'
	import mySlider from './Slider.vue'
	export default {
		name: 'App',
		components: {
			myCert,
			mySlider
		},
		
	}
</script>

<style>
	* {
		margin: 0;
		padding: 0;
		list-style: none;
		text-decoration: none;
	}
	#app{
		margin-top: 20px;
		width: 1000px;
		height: 1000px;
	}
</style>