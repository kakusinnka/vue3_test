<template>
  <div>
    <h2>子组件计数器：{{ count }}</h2>
    <button @click="increment">增加</button>
    <button @click="decrement">减少</button>
    <button @click="reset">重置</button>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { useCounter } from "../hooks/useCounter.js";

export default defineComponent({
  name: "ChildComponent",
  setup() {
    // 使用自定义 Hook
    const { count, increment, decrement, reset } = useCounter(5);

    return { count, increment, decrement, reset };
  },
});
</script>
