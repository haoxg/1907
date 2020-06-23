<template>
  <div class="trfer">
    <div class="lf_mu">
      <header>列表1</header>
      <ul>
        <li v-for="(i,$index) in show_lf" :key="$index">
          <input type="checkbox" v-model="left_data" :value="$index" />
          备选项{{i}}
        </li>
      </ul>
    </div>
    <div class="con">
      <button @click="add_lf">到左边</button>
      <button @click="add_rg">到右边</button>
    </div>
    <div class="rg_mu">
      <header>列表2</header>
      <ul>
        <li v-for="(i,$index) in show_rg" :key="$index">
          <input type="checkbox" v-model="right_data" :value="$index" />
          备选项{{i}}
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: "transfer",
  props: {
    data: {}
  },
  data() {
    return {
      show_lf: this.data,
      show_rg: [],
      left_data: [],
      right_data: []
    };
  },
  methods: {
    add_rg() {
      this.left_data.sort(function(a, b) {
        return b-a;
      });
      this.left_data.forEach(item => {
        this.show_rg.push(this.show_lf[item]);
        this.show_lf.splice(item, 1);
        this.left_data = [];
      });
    },
    add_lf() {
      this.right_data.sort(function(a, b) {
        return b-a;
      });
      this.right_data.forEach(item => {
        this.show_lf.push(this.show_rg[item]);
        this.show_rg.splice(item, 1);
        this.right_data = [];
      });
    }
  }
};
</script>
<style lang="scss">
.trfer {
  width: 700px;
  margin: auto;
  display: flex;
  border: 1px solid #e4e7ed;
  justify-content: space-between;
  padding: 20px 0px;
  border-radius: 15px;

  .lf_mu,
  .rg_mu {
    flex: 40%;
  }

  .con {
    text-align: center;
    display: flex;
    align-items: center;
    button {
      margin-right: 5px;
    }
  }
}
</style>
