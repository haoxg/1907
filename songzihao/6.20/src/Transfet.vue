<template>
	<div>
		<ul>
			<span>全选</span>
			<li v-for="(item,$index) in left" :key='item' @click="lnum=$index" :class="lnum==$index?'active':''">{{item}}</li>
		</ul>
		<input type="button" value="<" @click='rh' />   
		<input type="button" value=">" @click='le'/>
		<ul>
			<span>全选</span>
			<li v-for="(i,$index) in right" :key="i" @click="rnum=$index" :class="rnum==$index?'active':''">{{i}}</li>
		</ul>
	</div>
</template>

<script>
	export default {
		data() {
				return {
					lnum: 0,
					rnum: 0,
					left: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
					right: [3, 6, 8, 4, 2]
				}
			},
			methods: {
				
				le() {
					
					this.left.forEach(item => {
						this.right.push(this.left[item]);
						this.left.splice(item,1);
					});
				},
				rh(){
					this.right.forEach(item => {
						this.left.push(this.left[item]);
						this.right.splice(item,1);
					});
				}
			}
	}
</script>

<style scoped="scoped">
	* {
		list-style: none;
		padding: 0;
	}
	div{
		margin-right: 50px;
	}
	ul {
		float: left;
		width: 150px;
		border: 1px solid gainsboro;
		border-radius: 5px;
	}
	
	li {
		width: 150px;
		text-align: center;
		margin-top: 2px;
	}
	
	input {
		float: left;
		margin-top: 60px;
		width: 40px;
		height: 40px;
		background-color: dodgerblue;
		color: white;
		font-size: 20px;
		border: none;
		border-radius: 5px;
		margin: 50px 5px 0 5px;
	}
	
	span {
		margin-left: 40%;
		text-align: center;
	}
	
	.active {
		color: cornflowerblue;
		background-color: gainsboro;
	}
</style>