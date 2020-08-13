<template>
  <div class="home">
    <!-- 首页  一开始的布局就没布局好导致后来布局没时间改了。-->
    <div class="myhome">数据中心</div>
    <el-menu
      :default-active="activeIndex2"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b"
    >
      <el-menu-item index="1">处理中心</el-menu-item>
      <el-menu-item index="2">消息中心</el-menu-item>
      <el-menu-item index="3">订单管理echart</el-menu-item>
    </el-menu>

    <HelloWorld v-if="msg==3" :msg="msg" />
  </div>
</template>

<script>
import { NavMenu } from "element-ui";
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
  },
  data() {
    return {
      activeIndex: "1",
      activeIndex2: "1",
      msg: "",
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
      this.msg = key;
    },
  },
};
</script>
<style lang="less" >
.home {
  .el-menu-demo /deep/ {
    display: flex;
    justify-content: start;

    div {
      width: 15%;
      color: white;
      border: none;
    }
  }
}
</style>