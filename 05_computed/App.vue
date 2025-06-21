<template>
  <label for="">修改姓：</label>
  <input type="text" v-model="person.lastName" />
  <br />
  <label for="">修改名：</label>
  <input type="text" v-model="person.firstName" />
  <br />
  <label for="">修改姓名：</label>
  <input type="text" v-model="person.fullName" />
  <h1>我的姓是：{{ person.lastName }}</h1>
  <h1>我的名是：{{ person.firstName }}</h1>
  <h1>我的全名是：{{ person.fullName }}</h1>
</template>

<script>
import { reactive, computed } from "vue";

export default {
  name: "App",
  setup() {
    let person = reactive({
      lastName: "张",
      firstName: "三",
    });

    // 定义只读计算属性
    // person.fullName = computed(() => {
    //   return person.lastName + "-" + person.firstName;
    // });

    // 定义可写计算属性
    person.fullName = computed({
      get() {
        return `${person.lastName}-${person.firstName}`;
      },
      set(newValue) {
        const names = newValue.split("-");
        if (names.length === 2) {
          person.lastName = names[0];
          person.firstName = names[1];
        }
      },
    });

    return {
      person,
    };
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
