<template>
  <div>
    InputNumber Demo
    <div v-for="(item,index) in list" :key="index">
      <div>计数器{{index}}</div>
      <input-number  
      :value = item
      :step = 2
      :max = 99
      :min = 1
      :itemIndex = index
      @subNum='subNum' 
      @addNum='addNum' 
      @inputChange='inputChange'>
      </input-number>
    </div>
  </div>
</template>

<script>
import InputNumber from "@/components/inputNumber.vue";
export default {
  name: "HelloWorld",
  components: {
    InputNumber
  },
  data() {
    return {
      list: [10, 20, 25, 14],
    };
  },
  methods: {
    subNum(item) {
      console.log("subNum ***number:"  + item.inputNumber + ',index:' + item.itemIndex)
    },
    addNum(item) {
        console.log("addNum ***number:"  + item.inputNumber + ',index:' + item.itemIndex)
    },
    inputChange(item) {
      console.log("inputChange ***number:"  + item.inputNumber + ',index:' + item.itemIndex)
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
