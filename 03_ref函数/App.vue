<template>
  <h1>我叫：{{ name }}</h1>
  <h1>我今年：{{ age }}岁</h1>
  <h1>我的车是：{{ car.brand }}</h1>
  <h1>车的颜色是：{{ car.color }}</h1>
  <h1>车的价格是：{{ car.price }}</h1>
  <button @click="changeInfo">点击我修改信息</button>
</template>

<script>
import { ref } from "vue";

export default {
  name: "App",
  setup() {
    let name = ref("张三");
    let age = ref(18);
    let car = ref({
      brand: "宝马",
      color: "红色",
      price: 30,
    });

    const changeInfo = () => {
      name.value = "李四";
      age.value = 20;
      car.value.brand = "奔驰";
      car.value.color = "蓝色";
      car.value.price = 50;
    };

    return {
      name,
      age,
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
