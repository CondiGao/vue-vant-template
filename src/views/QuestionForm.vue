<template>
  <div>
    <van-nav-bar title="小花卷" left-arrow @click-left="onClickLeft" />
    <div id="question">
      <div v-if="current === 0 ">
        <van-panel title="体力活动" desc :status="(current+1) + '/4'">
          <div class="van-panel-content">您平时体力活动情况如何？</div>
          <div class="van-panel-footer" slot="footer">
            <van-button @click="nextStep" size="small">轻体力</van-button>
            <van-button @click="nextStep" size="small">中体力</van-button>
            <van-button @click="nextStep" size="small">重体力</van-button>
          </div>
        </van-panel>
      </div>
      <div v-if="current === 1 ">
        <van-panel title="喜好食物" desc :status="(current+1) + '/4'">
          <div class="van-panel-content">您平时喜欢吃哪些食物？</div>
          <div class="van-panel-footer" slot="footer">
            <van-button @click="nextStep" size="small">红肉</van-button>
            <van-button @click="nextStep" size="small">白肉</van-button>
            <van-button @click="nextStep" size="small">鱼虾/海鲜</van-button>
            <van-button @click="nextStep" size="small">素食主义</van-button>
          </div>
        </van-panel>
      </div>
      <div v-if="current === 2 ">
        <van-panel title="禁忌食物" desc :status="(current+1) + '/4'">
          <div class="van-panel-content">您平时不喜欢/过敏哪些食物？</div>
          <div class="van-panel-footer" slot="footer">
            <van-button @click="nextStep" size="small">红肉</van-button>
            <van-button @click="nextStep" size="small">白肉</van-button>
            <van-button @click="nextStep" size="small">鱼虾/海鲜</van-button>
            <van-button @click="nextStep" size="small">素食主义</van-button>
          </div>
        </van-panel>
      </div>
      <div v-if="current === 3 ">
        <van-panel title="孕期症状" desc :status="(current+1) + '/4'">
          <div class="van-panel-content">您在孕期内有哪些症状</div>
          <div class="van-panel-footer" slot="footer">
            <van-button @click="nextStep" size="small">孕吐严重</van-button>
            <van-button @click="nextStep" size="small">糖尿病</van-button>
            <van-button @click="nextStep" size="small">乳糖不耐受</van-button>
            <van-button @click="nextStep" size="small">其他</van-button>
          </div>
        </van-panel>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Step, Steps, Panel, Button, NavBar } from 'vant'

export default {
  components: {
    [Step.name]: Step,
    [Steps.name]: Steps,
    [Panel.name]: Panel,
    [Button.name]: Button,
    [NavBar.name]: NavBar
  },
  data() {
    return {
      current: 0,
      formInfo: {}
    }
  },
  methods: {
    nextStep() {
      if (this.current < 4) {
        this.current += 1
      }
    },
    onClickLeft() {
      if (this.current !== 0) {
        this.current = this.current - 1
      }
    }
  }
}
</script>

<style lang="less">
// body {
//   font-size: 16px;
//   background-color: #f8f8f8;
//   -webkit-font-smoothing: antialiased;
// }
.van-panel-footer {
  text-align: right;
  .van-button {
    margin-left: 5px;
  }
}
.van-panel-content {
  padding: 20px;
}
</style>
