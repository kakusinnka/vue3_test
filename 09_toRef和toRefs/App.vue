<template>
  <div>
    <h1>Vue 3 toRef 和 toRefs 示例</h1>

    <h2>toRef 示例</h2>
    <ToRefExample />

    <hr />

    <h2>toRefs 示例</h2>
    <ToRefsExample />

    <hr />

    <h2>响应式属性传递示例</h2>
    <ParentComponent />
  </div>
</template>

<script>
import ToRefExample from "./components/ToRefExample.vue";
import ToRefsExample from "./components/ToRefsExample.vue";
import ParentComponent from "./components/ParentComponent.vue";

export default {
  name: "App",
  components: {
    ToRefExample,
    ToRefsExample,
    ParentComponent,
  },
};
</script>
