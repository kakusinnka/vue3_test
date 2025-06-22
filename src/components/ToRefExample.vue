<template>
  <div>
    <p>名称：{{ state.name }}</p>
    <p>名称：{{ name }}</p>
    <button @click="changeName">修改名称</button>
  </div>
</template>
  
  <script>
import { reactive, toRef } from "vue";

export default {
  name: "ToRefExample",
  setup() {
    const state = reactive({
      name: "Vue 3",
      age: 3,
    });

    // 使用 toRef 将 state.name 转换为一个 ref
    const name = toRef(state, "name");

    const changeName = () => {
      name.value = "Vue 3.2"; // 修改 ref 会同步影响原始对象
    };

    return { state, name, changeName };
  },
};
</script>
  