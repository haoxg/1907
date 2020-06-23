<template>
    <div id="app">
        <div class="box">
            <div class="myLeftArr">
                <div class="tp">
                    <span>左边</span>
                </div>
                <div class="gd">0/4</div>
                <div class="tp" v-for="(item1,index1) in myLeftArr" :key="item1.id">
                    <label>
                        <input type="checkbox" v-model="leftArr" :value="index1"/>
                        <span>{{item1.num}}</span>
                    </label>
                </div>
            </div>
            <div class="ct">
                <span @click="pre"> ←</span>
                <span @click="next"> →</span>
            </div>
            <div class="myRightArr">
                <div class="tp">
                    <span>右边</span>
                </div>
                <div class="gd">0/4</div>
                <div class="tp" v-for="(item2,index2) in myRightArr" :key="item2.id">
                    <label>
                        <input type="checkbox" v-model="rightArr" :value="index2"/>
                        <span>{{item2.num}}</span>
                    </label>
                </div>
            </div>
        </div>
    </div>
</template>



<script>
    export default {
        data() {
            return {
                myLeftArr: [
                    { id: 1, num: "左1" },
                    { id: 2, num: "左2" },
                    { id: 3, num: "左3" },
                    { id: 4, num: "左4" }
                ],
                myRightArr: [
                    { id: 1, num: "右1" },
                    { id: 2, num: "右2" },
                    { id: 3, num: "右3" },
                    { id: 4, num: "右4" }
                ],
                leftArr: [],
                rightArr: []
            };
        },
        methods: {
            ll:function(){
                return this.leftArr.sort(this.ll);
            },
            next() {
                // 遍历leftArr
                this.leftArr.forEach(item => {
                    // myLeftArr.item添加到myRightArr里
                    this.myRightArr.push(this.myLeftArr[item]);
                    // 截取
                    this.myLeftArr.splice(item, 1);
                });
                // 置空
                this.leftArr = [];
            },
            pre() {
                // 遍历rightArr
                this.rightArr.forEach(item =>{
                    this.myLeftArr.push(this.myRightArr[item]);
                    this.myRightArr.splice(item,1)
                });
                this.rightArr=[]
            },
        }
    };
</script>






<style>
    html,body {
        margin: 0;
        padding: 0;
        user-select: none;
    }
    .box {
        width: 800px;
        height: 360px;
        margin: auto;
        padding: 20px;
    }
    .myLeftArr {
        width: 200px;
        height: 360px;
        border: 1px solid gray;
        float: left;
    }
    .ct {
        width: 140px;
        height: 50px;
        float: left;
        text-align: center;
        padding: 156px 40px;
    }
    .ct span {
        width: 60px;
        height: 40px;
        float: left;
        margin: 0 5px;
        line-height: 40px;
        color: whitesmoke;
        cursor: pointer;
        border-radius: 10px;
        background-color: rgba(0, 0, 0, 0.2);
        display: inline-block;
    }
    .myRightArr {
        width: 200px;
        height: 360px;
        border: 1px solid gray;
        float: left;
    }
    .tp {
        width: 100px;
        height: 20px;
        padding: 10px;
        float: left;
    }
    .tp input {
        width: 14px;
        height: 14px;
        text-align: left;
        margin-right: 5px;
    }
    .tp span {
        font-size: 16px;
        color: #303133;
        font-weight: 400;
    }
    .tp span:hover {
        color: #409eff;
    }
    .gd {
        color: #909399;
        font-size: 12px;
        font-weight: 400;
        float: right;
        padding: 10px;
        display: inline-block;
    }
</style>