<template>
  <MyHeader></MyHeader>
  <router-view />
  <MyFooter></MyFooter>
</template>
<script>
import MyHeader from "./MyHeader.vue";
import MyFooter from "./MyFooter.vue";
export default {
  name: "App",
  components: {
    MyHeader,
    MyFooter,
  },
};
</script>
