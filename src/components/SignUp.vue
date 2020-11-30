<template>
  <div>
    <div class="join-in">
      <el-button type="primary" @click="btnClick">加入我们</el-button>
    </div>
    <div class="sign-up-page">
      <el-dialog
        :visible="isVisible"
        :destroy-on-close="true"
        :center="true"
        width="40vw"
        @close="dialogClose"
      >
        <span class="dialog-title" slot="title">NetUnion 2020</span>
        <sign-up-form/>
      </el-dialog>
    </div>
  </div>
</template>

<script>
import SignUpForm from "./SignUpForm.vue";

export default {
  name: "SignUp",
  components: {
    SignUpForm,
  },
  data() {
    return {
      isVisible: false
    };
  },
  methods: {
    btnClick() {
      this.isVisible = true;
    },
    dialogClose() {
      this.isVisible = false;
    }
  },
};
</script>

<style scoped>
.join-in {
  position: fixed;
  width: fit-content;
  height: fit-content;
  right: 20px;
  top: 2px;
}

.dialog-title {
  font-size: 25px;
  font-weight: 600;
  line-height: 1.5em;
}
</style>
