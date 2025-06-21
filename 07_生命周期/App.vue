<template>
  <div>
    <h1>Vue 3 生命周期钩子函数练习</h1>
    <p>组件状态：{{ status }}</p>
    <button @click="toggleComponent">切换子组件显示/隐藏</button>
    <hr />
    <ChildComponent v-if="showChild" />
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
import ChildComponent from "./components/ChildComponent.vue";

export default {
  name: "App",
  components: { ChildComponent },
  setup() {
    const showChild = ref(true);
    const status = ref("初始化中...");
    let isUpdating = false; // 添加标志避免递归更新

    // 生命周期钩子函数
    onBeforeMount(() => {
      console.log("父组件 - onBeforeMount：组件即将挂载");
      status.value = "即将挂载";
    });

    onMounted(() => {
      console.log("父组件 - onMounted：组件已挂载");
      status.value = "已挂载";
    });

    onBeforeUpdate(() => {
      console.log("父组件 - onBeforeUpdate：组件即将更新");
      // 只在非更新状态时修改状态
      if (!isUpdating) {
        isUpdating = true;
        // 不在这里修改 status，避免触发新的更新循环
      }
    });

    onUpdated(() => {
      console.log("父组件 - onUpdated：组件已更新");
      // 重置标志，允许下一次更新
      isUpdating = false;
      // 不在这里修改 status，避免触发新的更新循环
    });

    onBeforeUnmount(() => {
      console.log("父组件 - onBeforeUnmount：组件即将卸载");
      status.value = "即将卸载";
    });

    onUnmounted(() => {
      console.log("父组件 - onUnmounted：组件已卸载");
      status.value = "已卸载";
    });

    // 切换子组件显示/隐藏
    const toggleComponent = () => {
      showChild.value = !showChild.value;
      // 在这里更新状态，而不是在更新钩子中
      status.value = showChild.value ? "显示子组件" : "隐藏子组件";
    };

    return { showChild, status, toggleComponent };
  },
};
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