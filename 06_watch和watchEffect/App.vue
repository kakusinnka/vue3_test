<template>
  <h1>示例 1：监听单一响应式数据</h1>
  <h1>Count：{{ count }}</h1>
  <button @click="count++">点我 Count 加 1 。</button>
  <hr />

  <h1>示例 2：监听多个数据源</h1>
  <h1>我的名字是：{{ lastName }}, {{ firstName }}</h1>
  <button
    @click="
      lastName = lastName + '~';
      firstName = firstName + '!';
    "
  >
    点我修改名字。
  </button>
  <hr />

  <h1>示例 3：监听复杂的 reactive 对象</h1>
  <h1>我的名字是：{{ user.lastName }}, {{ user.firstName }}</h1>
  <h1>我的今年：{{ user.age }} 岁。</h1>
  <button
    @click="
      user.lastName = user.lastName + '~';
      user.firstName = firstName + '!';
    "
  >
    点我修改名字。
  </button>
  <hr />

  <h1>自动追踪依赖</h1>
  <h1>Count：{{ count }}</h1>
  <h1>Count 乘2：{{ doubleCount }}</h1>
  <button @click="count++">点我 Count 加 1 并乘以 2。</button>
</template>

<script>
import { ref, reactive, watch, watchEffect } from "vue";

export default {
  name: "App",
  setup() {
    const count = ref(0);
    const doubleCount = ref(0);

    // 使用 watch 监听 count 的变化
    watch(count, (newValue, oldValue) => {
      console.log(`Count changed from ${oldValue} to ${newValue}`);
    });

    const firstName = ref("John");
    const lastName = ref("Doe");

    // 监听多个数据源
    watch(
      [firstName, lastName],
      ([newFirstName, newLastName], [oldFirstName, oldLastName]) => {
        console.log(
          `First Name changed from ${oldFirstName} to ${newFirstName}`
        );
        console.log(`Last Name changed from ${oldLastName} to ${newLastName}`);
      }
    );

    const user = reactive({
      firstName: "John",
      lastName: "Doe",
      age: 30,
    });

    // 监听整个 reactive 对象
    watch(
      () => user,
      (newUser, oldUser) => {
        console.log("User changed:", newUser, oldUser);
      },
      { deep: true } // 深度监听
    );

    // 监听整个 reactive 对象
    watchEffect(() => {
      doubleCount.value = count.value * 2;
    });

    // 返回数据用于模板
    return { count, firstName, lastName, user, doubleCount };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
