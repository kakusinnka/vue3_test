<!-- ChildComponent.vue -->
<template>
  <div>
    <h2>我是子组件</h2>
    <p>当前时间：{{ currentTime }}</p>
  </div>
</template>
  
  <script>
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";

export default {
  name: "ChildComponent",
  setup() {
    const currentTime = ref(new Date().toLocaleTimeString());

    // 生命周期钩子函数
    onBeforeMount(() => {
      console.log("子组件 - onBeforeMount：组件即将挂载");
    });

    onMounted(() => {
      console.log("子组件 - onMounted：组件已挂载");
    });

    onBeforeUpdate(() => {
      console.log("子组件 - onBeforeUpdate：组件即将更新");
    });

    onUpdated(() => {
      console.log("子组件 - onUpdated：组件已更新");
    });

    onBeforeUnmount(() => {
      console.log("子组件 - onBeforeUnmount：组件即将卸载");
    });

    onUnmounted(() => {
      console.log("子组件 - onUnmounted：组件已卸载");
    });

    return { currentTime };
  },
};
</script>