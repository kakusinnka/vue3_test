<template>
  <div>
    <h2>shallowRef 示例</h2>
    <p>顶层值：{{ shallow.name }}</p>
    <p>嵌套值：{{ shallow.details.version }}</p>
    <button @click="updateTopLevel">更新顶层值</button>
    <button @click="updateNestedProperty">更新嵌套属性</button>
  </div>
</template>
  
  <script>
import { shallowRef } from "vue";

export default {
  name: "ShallowRefExample",
  setup() {
    const shallow = shallowRef({ name: "Vue", details: { version: "3.0" } });

    const updateTopLevel = () => {
      shallow.value = { name: "Vue 3", details: { version: "3.2" } }; // 触发更新
    };

    const updateNestedProperty = () => {
      shallow.value.details.version = "3.3"; // 不会触发更新
    };

    return { shallow, updateTopLevel, updateNestedProperty };
  },
};
</script>
  