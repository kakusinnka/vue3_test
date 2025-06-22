<template>
  <div>
    <p>名称：{{ state.name }}</p>
    <p>年龄：{{ state.age }}</p>
    <p>名称：{{ name }}</p>
    <p>年龄：{{ age }}</p>
    <button @click="changeName">修改名称</button>
    <button @click="changeAge">修改年龄</button>
  </div>
</template>
  
  <script>
import { reactive, toRefs } from "vue";

export default {
  name: "ToRefsExample",
  setup() {
    const state = reactive({
      name: "Vue 3",
      age: 3,
    });

    // 使用 toRefs 将 state 的所有属性转换为 ref
    const { name, age } = toRefs(state);

    const changeName = () => {
      name.value = "Vue 3.2"; // 修改 ref 会同步影响原始对象
    };

    const changeAge = () => {
      age.value++; // 修改 ref 会同步影响原始对象
    };

    return { state, name, age, changeName, changeAge };
  },
};
</script>
  