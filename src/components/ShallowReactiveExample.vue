<template>
  <div>
    <h2>shallowReactive 示例</h2>
    <p>顶层值：{{ shallow.name }}</p>
    <p>嵌套值：{{ shallow.details.version }}</p>
    <button @click="updateTopLevel">更新顶层值</button>
    <button @click="updateNestedProperty">更新嵌套属性</button>
  </div>
</template>
  
  <script>
import { shallowReactive } from "vue";

export default {
  name: "ShallowReactiveExample",
  setup() {
    const shallow = shallowReactive({
      name: "Vue",
      details: {
        version: "3.0",
        features: ["Composition API", "Teleport"],
      },
    });

    const updateTopLevel = () => {
      shallow.name = "Vue 3"; // 触发更新
    };

    const updateNestedProperty = () => {
      shallow.details.version = "3.3"; // 不会触发更新
    };

    return { shallow, updateTopLevel, updateNestedProperty };
  },
};
</script>
  