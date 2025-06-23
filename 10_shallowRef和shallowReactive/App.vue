<template>
  <div>
    <ShallowRefExample />
    <hr />
    <ShallowReactiveExample />
  </div>
</template>

<script>
import ShallowRefExample from "./components/ShallowRefExample.vue";
import ShallowReactiveExample from "./components/ShallowReactiveExample.vue";

export default {
  name: "App",
  components: {
    ShallowRefExample,
    ShallowReactiveExample,
  },
};
</script>
