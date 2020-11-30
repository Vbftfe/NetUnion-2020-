<template>
  <div class="sign-up-form">
    <el-form
      :model="form"
      :rules="rules"
      @validate="validateForm"
      class="form"
      ref="form"
    >
      <el-form-item label="姓名" prop="name">
        <el-input v-model="form.name"></el-input>
      </el-form-item>
      <el-form-item label="学号" prop="studentNum">
        <el-input v-model="form.studentNum"></el-input>
      </el-form-item>
      <el-form-item label="邮箱" prop="email">
        <el-input v-model="form.email" type="email"></el-input>
      </el-form-item>
      <el-form-item label="方向" prop="direction">
        <el-select v-model="form.direction" placeholder="请选择">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value"
          ></el-option>
        </el-select>
      </el-form-item>
    </el-form>
    <div class="upload">
      <span>附件上传</span>
      <el-upload
        class="upload-demo"
        action="http://localhost:3000/file"
        :on-preview="handlePreview"
        :on-remove="handleRemove"
        multiple
        :limit="3"
        :on-exceed="handleExceed"
        :file-list="fileList"
        ref="upload"
      >
        <el-button size="small" type="primary">点击上传</el-button>
        <div slot="tip" class="el-upload__tip">
          支持上传word、pdf、markdown等附件
        </div>
      </el-upload>
    </div>
    <div class="submit">
      <el-button type="primary" @click="submit" :disabled="!isCorrect"
        >提交</el-button
      >
    </div>
    <div class="query">
      <el-button size="small" @click="query" :disabled="!isQuery"
        >查询</el-button
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "SignUpForm",
  data() {
    return {
      fileList: [],
      form: {
        name: "",
        studentNum: "",
        email: "",
        direction: "",
      },
      rules: {
        name: [{ required: true, message: "请输入姓名", trigger: "blur" }],
        studentNum: [
          { required: true, message: "请输入学号", trigger: "blur" },
          { validator: this.validateStudentNum, trigger: "blur" },
        ],
        email: [{ required: true, message: "请输入邮箱", trigger: "blur" }],
        direction: [
          { required: true, message: "请选择方向", trigger: "change" },
        ],
      },
      options: [
        {
          value: "网络方向",
          label: "网络方向",
        },
        {
          value: "前端方向",
          label: "前端方向",
        },
        {
          value: "DevOps方向",
          label: "DevOps方向",
        },
        {
          value: "文宣方向",
          label: "文宣方向",
        },
      ],
      isCorrect: false,
      counter: 0,
      isQuery: false,
    };
  },
  methods: {
    validateStudentNum(rule, value, callback) {
      value = value.trim();
      if (!/^[0-9]{13}$/.test(value)) {
        callback(new Error("学号应为长度13的数字"));
      } else {
        callback();
      }
    },
    handleRemove(file, fileList) {
      console.log(file, fileList);
    },
    handlePreview(file) {
      console.log(file);
    },
    handleExceed(files, fileList) {
      this.$message.warning(
        `当前限制选择 3 个文件，本次选择了 ${files.length} 个文件，共选择了 ${
          files.length + fileList.length
        } 个文件`
      );
    },
    submit() {
      if (!this.fileList.length) {
        this.$refs.upload.submit();
      }
      this.storeMess();
      fetch("http://localhost:3000/loginMess", {
        method: "post",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(this.form),
      }).then((res) => {
        if (res.ok) {
          this.$message({
            message: "提交成功",
            type: "success",
          });
        }
      });
    },
    validateForm(...args) {
      if (args[1]) {
        this.counter = this.counter + 1;
      }
      if (this.counter >= 4) {
        this.isCorrect = true;
        this.counter = 0;
      } else {
        this.isCorrect = false;
      }
      if (this.form.studentNum !== "") {
        this.isQuery = true;
      }
    },
    storeMess() {
      //将用户信息保存到localStroage中
      if (this.form.studentNum !== "") {
        localStorage.setItem(this.form.studentNum, JSON.stringify(this.form));
      }
    },
    query() {
      let str = localStorage.getItem(this.form.studentNum);
      console.log(str);
      if (!!str) {
        this.form = JSON.parse(str);
        this.$message({
          message: '查询成功',
          type: 'success'
        });
        this.$refs.form.clearValidate();
      } else {
        this.$message({
          message: '查询失败',
          type: 'error'
        });
        this.$refs.form.clearValidate();
      }
    },
  },
};
</script>

<style scoped>
.sign-up-form {
  width: 20vw;
  margin: 0 auto;
  height: 65vh;
}

.submit {
  width: fit-content;
  margin: 0 auto;
}

.upload span {
  line-height: 3em;
}

.query {
  position: absolute;
  right: 60px;
  top: 28vh;
}
</style>
