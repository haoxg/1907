<template>
  <div class="slider_wp">
    <div class="slider">
      <div class="bar" @mousedown="bar_move" ref="bar" @mouseover="over" @mouseout="out"></div>
      <div class="go"></div>
      <div class="num" v-if="show_num" ref="num">{{now_num}}</div>
      <div class="count" ref="count" v-if="show_input">
        <button @click="now_num<=0?now_num=0:now_num--,update()">-</button>
        <input type="text" v-model="now_num" />
        <button @click="now_num>=max?now_num=max:now_num++ ,update()">+</button>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "slider",
  props: {
    de_num: {
      //初始化位置
      default: 0
    },
    max: {
      default: 100 //最大值
    },
    show_num: {
      default: true //是否显示数字
    },
    show_input: {
      default: false
    } //是否显示input输入框
  },
  data() {
    return {
      now_num: this.de_num,
      maxWidth: ""
    };
  },

  methods: {
    bar_move(e) {
      //bar移动
      let evt = e || event;
      let now_sl = this.$refs.bar; //当前点击的元素
      let down_x = now_sl.offsetParent.offsetLeft + evt.offsetX;
      window.onmousemove = e => {
        let evt = e || event;
        var moveX = evt.clientX - down_x;
        moveX = moveX <= 0 ? 0 : moveX;
        moveX = moveX >= this.maxWidth ? this.maxWidth : moveX;
        now_sl.style.left = moveX + "px";
        now_sl.nextElementSibling.style.width = moveX + 16 + "px";
        this.now_num = parseInt((moveX / this.maxWidth) * this.max);
        this.$refs.num.style.left = moveX + "px";
      };
      window.onmouseup = function() {
        window.onmousemove = null;
      };
    },
    update() {
      //第一次渲染
      let bar = this.$refs.bar;
      this.maxWidth = bar.offsetParent.clientWidth - bar.clientWidth; //最大的距离
      let changeX = (this.maxWidth / this.max) * this.now_num;
      bar.style.left = changeX + "px";
      bar.nextElementSibling.style.width = changeX + 16 + "px";
      this.$refs.num.style.left = changeX + "px";
    },
    over() {
      this.$refs.num.style.display = "block";
    },
    out() {
      this.$refs.num.style.display = "none";
    },
    change() {
      //自定义chang事件
    //   console.log(1);
      //   onmouseup = function(param) {
      //     //   s
      //   };
    }
  },

  mounted() {
    this.update();
    this.$emit("change", 1);
  }
};
</script>


<style lang="scss">
.slider_wp {
  height: 30px;
  margin: 30px;
  .slider {
    height: 8px;
    width: 420px;
    background-color: #e4e7ed;
    border-radius: 25px;
    position: relative;
    .num {
      height: 20px;
      width: 20px;
      color: white;
      background-color: black;
      position: absolute;
      top: -26px;
      font-size: 12px;
      line-height: 20px;
      border-radius: 5px;
      display: none;
    }
    .count {
      width: 70px;
      position: absolute;
      left: 440px;
      top: -5px;
      button {
        width: 20px;
      }
      input {
        width: 30px;
        box-sizing: border-box;
        text-align: center;
      }
    }
    .go {
      background-color: #409eff;
      height: 100%;
      width: 0px;
      position: absolute;
      left: 0px;
      top: 0px;
      border-radius: 25px;
      width: 16px;
      z-index: 1;
    }
    .bar {
      height: 20px;
      width: 20px;
      cursor: pointer;
      border-radius: 50px;
      border: 2px solid #409eff;
      position: absolute;
      background-color: white;
      top: -5px;
      z-index: 2;
      box-sizing: border-box;
    }
  }
}
</style>