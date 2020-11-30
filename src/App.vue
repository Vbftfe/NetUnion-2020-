<template>
  <div id="app">
    <introduction />
    <sign-up />
  </div>
</template>

<script>
import SignUp from "./components/SignUp.vue";
import Introduction from "./components/Introduction.vue";

export default {
  name: "App",
  components: {
    SignUp,
    Introduction,
  },
  data() {
    return {};
  },
  beforeMount() {
    document.body.classList = "typora-export os-windows";
  },
};
</script>