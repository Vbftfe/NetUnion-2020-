<template>
  <!-- <el-upload
      class="upload-demo"
      action="http://localhost:3000/file"
      :on-preview="handlePreview"
      :on-remove="handleRemove"
      :before-remove="beforeRemove"
      multiple
      :limit="3"
      :on-exceed="handleExceed"
      :file-list="fileList"
      :auto-upload="true"
    >
      <el-button size="small" type="primary">点击上传</el-button>
      <div slot="tip" class="el-upload__tip">
        只能上传jpg/png文件，且不超过500kb
      </div>
    </el-upload>
    <el-button type="primary" @click="btnClick">发送</el-button> -->
  <div id="write" class="">
    <h1>
      <a name="netunion-2020-recruit" class="md-header-anchor"></a
      ><span>NetUnion 2020 recruit</span>
    </h1>
    <h2><a name="介绍" class="md-header-anchor"></a><span>介绍</span></h2>
    <p>
      <span
        >我们是成立
        23年的学生组织，历经变迁，现隶属于信息中心，参与校内网络基础设施维护工作，提供开源软件镜像等诸多服务。</span
      >
      <span>如果你想参与讨论、结识大佬，请点击 join.uestclug.org </span>
      <span>(</span
      ><a href="http://join.uestclug.org" target="_blank" class="url"
        >http://join.uestclug.org</a
      ><span>)加入这个大社团。</span>
      <span
        >如果你愿意出一份力来维系社区、维护服务，请继续阅读并完成招新学习任务。并以
        “NU招新 +姓名”为主题，发送 PDF格式简历至 </span
      ><a href="mailto:nu@uestclug.org" target="_blank" class="url"
        >nu@uestclug.org</a
      ><span> </span> <span>(</span
      ><a href="mailto:mailto:nu@uestclug.org" target="_blank" class="url"
        >mailto:nu@uestclug.org</a
      ><span>)，简历需包含所在学院、年级、个人简介以及意愿方向。</span>
    </p>
    <h2>
      <a name="我们要做的事" class="md-header-anchor"></a
      ><span>我们要做的事</span>
    </h2>
    <ul>
      <li><span>向校内外 提供开源软件镜像、在线文档、 IP电视等服务</span></li>
      <li><span>维护两校区学生宿舍区的网络基础设施</span></li>
    </ul>
    <h2>
      <a name="为什么加入nu" class="md-header-anchor"></a
      ><span>为什么加入NU</span>
    </h2>
    <ul>
      <li><span>办公处所位置便利，电力与网络顺畅稳定</span></li>
      <li><span>内部藏书种类繁多，团建活动定期举办</span></li>
      <li><span>够用的服务器资源，助你实现天才想法</span></li>
      <li><span>零距离接触生产环境网络设备的有趣经验</span></li>
      <li><span>勤工助学有偿服务机会</span></li>
    </ul>
    <h2>
      <a name="招新内容" class="md-header-anchor"></a><span>招新内容</span>
    </h2>
    <h3>
      <a name="基础部分" class="md-header-anchor"></a><span>基础部分</span>
    </h3>
    <ul>
      <li><span>计算机网络概览（《计算机网络自顶向下》第一章）</span></li>
    </ul>
    <ul>
      <li><span>常用 Linux命令</span></li>
    </ul>
    <h3>
      <a name="网络方向" class="md-header-anchor"></a><span>网络方向</span>
    </h3>
    <ul>
      <li><span>《计算机网络自顶向下》前六章</span></li>
    </ul>
    <ul>
      <li>
        <span>Wireshark用法在实习期现场教授交换机配置、网线制作等</span>
      </li>
    </ul>
    <h3>
      <a name="前端方向" class="md-header-anchor"></a><span>前端方向</span>
    </h3>
    <ul>
      <li><span>需要掌握 vue/react等框架中至少一个 </span></li>
    </ul>
    <ul>
      <li><span>Optional:拥有 UI组件框架使用经验</span></li>
    </ul>
    <h3>
      <a name="devops方向" class="md-header-anchor"></a><span>DevOps方向</span>
    </h3>
    <ul>
      <li><span>需要掌握至少一门后端语言 Optional</span></li>
      <li><span>容器或集群至少一方面使用经验</span></li>
    </ul>
    <h3>
      <a name="文宣方向" class="md-header-anchor"></a><span>文宣方向</span>
    </h3>
    <ul>
      <li><span>文案 /美工能力</span></li>
      <li><span>组织活动等</span></li>
    </ul>
  </div>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
      fileList: [],
    };
  }
};
</script>