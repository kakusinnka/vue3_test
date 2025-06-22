<template>
  <div>
    <h3>子组件</h3>
    <p>接收到的名称：{{ name }}</p>
    <button @click="tryModifyProps">尝试修改 name</button>
    <button @click="modifyLocalCopy">修改本地副本</button>
    <button @click="modifyNameByChild">修改名称（通过事件通知父组件）</button>
    <p>本地副本的名称：{{ localName }}</p>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "ChildComponent",
  props: {
    name: {
      type: String,
      required: true,
    },
  },
  emits: ["updateNameByChild"], // 声明自定义事件
  setup(props, { emit }) {
    // 创建一个本地副本，保持响应式
    const localName = ref(props.name);

    // 尝试直接修改 props（会触发 Vue 的警告）
    const tryModifyProps = () => {
      // eslint-disable-next-line
      props.name = "试图修改 props"; // 这会触发 Vue 的警告
    };

    // 修改本地副本
    const modifyLocalCopy = () => {
      localName.value = "修改了本地副本";
    };

    const modifyNameByChild = () => {
      const newName = "子组件修改的名称";
      emit("updateNameByChild", newName); // 通过事件将新名称传递给父组件
    };
    return { localName, tryModifyProps, modifyLocalCopy, modifyNameByChild };
  },
};
</script>
