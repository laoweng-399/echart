<template>
  <div class="chart">
    <!-- 左侧布局 刚开始的布局就存在问题后面没有时间改了-->
    <div class="zuo">
      <!-- 我参与的 -->

      <div class="myParticipation">
        <div>
          <span style="color:blue">我参与的</span>
        </div>
        <div class="myParticipationDetail">
          <div class="myParticipation-item" v-for="(item1,index1) of myParticipation" :key="index1">
            <div v-for="(item2,index2) of item1" :key="index2">
              <p v-if="index2!='precent'">{{index2}}........{{item2}}</p>
              <el-progress class="precent" v-else :percentage="item2"></el-progress>
            </div>
          </div>
        </div>
      </div>
      <div class="countEchart">
        <div style="color:blue">销售统计</div>
        <div id="myChart"></div>
      </div>
    </div>
  </div>
</template>

<script>
import { Progress } from "element-ui";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },

  data() {
    return {
      myParticipation: [
        {
          title: "8月",
          detail: "888888888888888888888",
          precent: 88,
        },
        {
          title: "7月",
          detail: "777777777777777777777",
          precent: 77,
        },
        {
          title: "6月",
          detail: "66666666666666666666",
          precent: 66,
        },
        {
          title: "5月",
          detail: "55555555555555555555",
          precent: 55,
        },
      ],
    };
  },
  mounted() {
    this.drawLine();
  },
  methods: {
    drawLine() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById("myChart"));
      // 绘制图表
      myChart.setOption({
        legend: {},
        tooltip: {},
        dataset: {
          dimensions: ["月份", "目标销售额", "当前销售额"],
          source: [
            {
              月份: "1月",
              目标销售额: 43.3,
              当前销售额: 85.8,
            },
            { 月份: "2月", 目标销售额: 83.1, 当前销售额: 73.4 },
            {
              月份: "3月",
              目标销售额: 86.4,
              当前销售额: 65.2,
            },
            {
              月份: "4月",
              目标销售额: 72.4,
              当前销售额: 53.9,
            },
          ],
        },
        xAxis: { type: "category" },
        yAxis: {},
        // Declare several bar series, each will be mapped
        // to a column of dataset.source by default.
        series: [{ type: "bar" }, { type: "bar" }],
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.zuo {
  width: 80%;
  .myParticipation {
    .myParticipationDetail {
      display: flex;
      justify-content: space-around;
      align-items: center;

      .myParticipationDeitem {
        padding: 30px;
        width: 100%;
      }
    }
    .myParticipation-item:nth-child(2) {
      background-color: red;
      border-radius: 3%;
    }
    .myParticipation-item:nth-child(1) {
      background-color: blue;
      border-radius: 3%;
    }
    .myParticipation-item:nth-child(3) {
      background-color: orange;
      border-radius: 3%;
    }
    .myParticipation-item:nth-child(4) {
      background-color: green;
      border-radius: 3%;
    }
  }
  .countEchart {
    border-radius: 5px;
    margin-top: 20px;
    #myChart {
      width: 100%;
      height: 400px;
      border: black 1px solid;
    }
  }
}
</style>
