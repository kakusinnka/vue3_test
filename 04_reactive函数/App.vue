<template>
  <h1>我的车是：{{ car.brand }}</h1>
  <h1>车的颜色是：{{ car.color }}</h1>
  <h1>车的价格是：{{ car.price }}</h1>
  <button @click="changeInfo">点击我修改信息</button>
</template>

<script>
import { reactive } from "vue";

export default {
  name: "App",
  setup() {
    let car = reactive({
      brand: "宝马",
      color: "红色",
      price: 30,
    });

    const changeInfo = () => {
      car.brand = "奔驰";
      car.color = "蓝色";
      car.price = 50;
    };

    return {
      car,
      changeInfo,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
