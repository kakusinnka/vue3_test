<template>
  <div>
    <h1>Vue 3 Hooks 示例</h1>
    <p>父组件计数器：{{ count }}</p>
    <button @click="increment">增加</button>
    <button @click="decrement">减少</button>
    <button @click="reset">重置</button>

    <hr />
    <ChildComponent />
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { useCounter } from "./hooks/useCounter.js";
import ChildComponent from "./components/ChildComponent.vue";

export default defineComponent({
  name: "App",
  components: { ChildComponent },
  setup() {
    // 使用自定义 Hook
    const { count, increment, decrement, reset } = useCounter(10);

    return { count, increment, decrement, reset };
  },
});
</script>


<style>
h1 {
  color: #42b983;
}
button {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background-color: #369f72;
}
</style>