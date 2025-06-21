<template>
  <h1>我叫：{{ name }}</h1>
  <h1>我今年{{ age }}岁</h1>
  <button @click="sayHello">点击我</button>
</template>

<script>
export default {
  name: "App",
  setup() {
    let name = "张三";
    let age = 18;

    const sayHello = () => {
      alert(`我叫${name}, 今年${age}岁`);
    };

    return {
      name,
      age,
      sayHello,
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
