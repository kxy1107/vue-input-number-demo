<template>
  <div>
    <span @click="clickSub" :class="[inputNumber > 1 ? '':'disabled-click']">-</span>
    <input type="text" pattern="[0-9]*" v-model="inputNumber" v-on:input ="changeInputNum" />
    <span @click="clickAdd" :class="[inputNumber >=99  ? 'disabled-click':'']">+</span>
  </div>
</template>

<script>
export default {
  name: "InputNumber",
  props: {
    value: {
      //绑定的输入框的值
      type: Number,
      default: 1
    },
    step:{
      type:Number,
      default:1,
    },
    max: {
      //输入框最大值
      type: Number,
      default: 99
    },
    min: {
      //输入框最小值
      type: Number,
      default: 1
    },
    addSubClass: {
      //加减的样式
      type: String,
      default: ""
    },
    inputClass: {
      //输入框样式
      type: String,
      default: ""
    },
    itemIndex: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      inputNumber:0,
    };
  },
  mounted(){
    this.inputNumber = this.value;
  },
  methods: {
    clickSub(e) {
      if (this.inputNumber <= this.min) {
        this.inputNumber == this.min
        return;
      }
      this.inputNumber -= this.step;
      let itemText = {
        inputNumber: this.inputNumber,
        itemIndex: this.itemIndex
      };
      this.$emit("subNum", itemText);
      // this.$emit("subNum", this.itemIndex);
    },
    clickAdd(e) {
      if (this.inputNumber >= this.max) {
        this.inputNumber == this.max
        return;
      }
      this.inputNumber += this.step;
      let itemText = {
        inputNumber: this.inputNumber,
        itemIndex: this.itemIndex
      };
      this.$emit("addNum", itemText);
      // this.$emit("addNum", this.itemIndex);
    },
    changeInputNum(e) {
      this.inputNumber = e.target.value.replace(/[^0-9.]/g, "");
      if (this.inputNumber * 1 >= this.max) {
        this.inputNumber = this.max;
      } else if (this.inputNumber * 1 <= this.min) {
        this.inputNumber = this.min;
      }
      console.log(this.inputNumber);
      let itemText = {
        inputNumber: this.inputNumber,
        itemIndex: this.itemIndex
      };
      this.$emit("inputChange", itemText);
    }
  }
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  display: flex;
  display: -webkit-flex;
}
span:first-child {
  display: inline-block;
  border: 1px solid #999;
  width: 1rem;
  height: 1rem;
  line-height: 1rem;
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
  cursor: pointer;
  text-align: center;
}
span:last-child {
  display: inline-block;
  border: 1px solid #999;
  width: 1rem;
  height: 1rem;
  line-height: 1rem;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
  cursor: pointer;
  text-align: center;
}
.disabled-click {
  cursor: not-allowed;
  color: #d2d2d2;
}
input {
  border-left: 0;
  border-right: 0;
  border-top: 1px solid #999;
  border-bottom: 1px solid #999;
  width: 1.5rem;
  text-align: center;
  font-size: 0.7rem;
  outline: none;
}
input:focus {
  outline: none;
}
</style>
