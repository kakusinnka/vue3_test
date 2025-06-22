<template>
  <div>
    <h2>父组件</h2>
    <p>父组件的名称：{{ name }}</p>
    <button @click="updateName">修改父组件名称</button>
    <ChildComponent :name="name" @updateNameByChild="updateNameByChild" />
  </div>
</template>
  
  <script>
import { reactive, toRef } from "vue";
import ChildComponent from "./ChildComponent.vue";

export default {
  name: "ParentComponent",
  components: { ChildComponent },
  setup() {
    const state = reactive({
      name: "Vue 3",
    });

    const name = toRef(state, "name");

    const updateName = () => {
      name.value = "Vue 3.2"; // 修改父组件的 name
    };

    const updateNameByChild = (newName) => {
      name.value = newName;
    };

    return { name, updateName, updateNameByChild };
  },
};
</script>
  