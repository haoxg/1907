<template>
	<div id="app">
		<!-- <img alt="Vue logo" src="./assets/logo.png"> -->

		<div class="container">
			<div class="left-transfer">
				<p><input type="checkbox" ref="leftAll" value="leftAll" v-model="allCheck"/>列表 1</p>
				<div class="left-list" ref="left">
					<HelloWorld :msg="item" v-for="item in oneList" :key="item" @bl="fn"/>
				</div>
			</div>
			<div class="middle-transfer">
				<div class="buttom" style="margin-top: 120px;">
					<button style="margin-right: 10px;" @click="toLeft">👈</button>
					<button @click="toRight">👉</button>
				</div>
			</div>
			<div class="right-transfer">
				<p><input type="checkbox" value="rightAll" v-model="allCheck"/>列表 2</p>
				<div class="right-list" ref="right"><HelloWorld :msg="item" v-for="item in twoList" :key="item" /></div>
			</div>
		</div>
	</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
	name: 'App',
	components: {
		HelloWorld
	},
	data() {
		return {
			oneList: ['备选项1', '备选项2', '备选项3', '备选项4', '备选项5', '备选项6', '备选项7', '备选项8', '备选项9', '备选项10'],
			twoList: ['备选项11', '备选项12', '备选项13'],
			allCheck:[],
			oneCheck:[]
		};
	},
	watch:{
		'allCheck'(){
			let leftDom=this.$refs.left.children
			let rightDom=this.$refs.right.children
			if(this.allCheck.includes('leftAll')){
				leftDom.forEach(item=>{item.children[0].checked=true})
			}else{
				leftDom.forEach(item=>{item.children[0].checked=false})
			}
			if(this.allCheck.includes('rightAll')){
				rightDom.forEach(item=>{item.children[0].checked=true})
			}else{
				rightDom.forEach(item=>{item.children[0].checked=false})
			}
		}
	},
	methods:{
		toLeft(){
			let rightDom=this.$refs.right.children
			var arr=[]
			rightDom.forEach((item,index)=>{
				if(item.children[0].checked==true){
					arr.push(this.twoList[index])
				}
			})
			this.oneList.push(...arr)
			this.twoList=this.twoList.filter(res=>{return !arr.includes(res)})
		},
		toRight(){
			let leftDom=this.$refs.left.children
			var arr=[]
			leftDom.forEach((item,index)=>{
				if(item.children[0].checked==true){
					arr.push(this.oneList[index])
				}
			})
			this.twoList.push(...arr)
			this.oneList=this.oneList.filter(res=>{return !arr.includes(res)})
		},
		fn(event){
			console.log(event)
		}
	}
};
</script>

<style>
.container {
	width: 500px;
	overflow: hidden;
}
.left-transfer {
	float: left;
	width: 200px;
}
.left-transfer > p,
.right-transfer > p {
	background-color: #ccc;
	line-height: 30px;
	padding-left: 10px;
}
.left-list,
.right-list {
	padding-left: 10px;
	overflow: scroll;
	height: 300px;
}
.left-list p,
.right-list p {
	line-height: 36px;
}
.left-list p:hover,
.right-list p:hover{
	color: red;
}
.middle-transfer {
	float: left;
	width: 100px;
	text-align: center;
}
.right-transfer {
	float: left;
	width: 200px;
}
.right-transfer > p {
	background-color: #ccc;
	line-height: 30px;
}
</style>
