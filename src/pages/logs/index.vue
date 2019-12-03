<template>
  <div class="container">
    <input class="input" placeholder="请输入问题后，随心按下按钮" v-model="keywords"/>
    <div class="askBtn" @click="getAns">search</div>
    <div class="ansWrapper" v-if="answer">
      <p class="pha">{{answer}}</p>
    </div>
    <div class="entryWrapper" v-if="entryShow">
      <div class="entryBtn" @click="goVersion1">第一版</div>
      <div class="entryBtn">第二版</div>
      <div class="entryBtn">第三版</div>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      keywords: '',
      entryShow: false,
      answer: '',
      ansList: ['只想不努力是没用的!!加油', '非常冒险...机会不大', '接受别人的意见会有助力', '办何自己不肯妥协，先问一下自已的能力', '毫无疑问', '仍然难以估计', '绝对不可', '耐心等待', '为何你还相信自己的幻想',
        '不要表态', '可能会造成震惊事件', '答案不是你所想但又会成功', '你需要尝试接受', '太疑神疑鬼了、加强自信吧', '是你心思误放在其它地方，影响运程', '别心急', '很大机会出现另一局面', '静观其变', '现在不是最佳时机',
        '保持警愓、并非如你所想', '听一下别人劝告吧', '现在没法要求太多', '用轻松的态度面对', '事与愿违，须多留意自己情绪', '要节制了，记得见好就收', '不在你控制范围以内', '小心', '继续走你的路，问题当没有事情发生过吧',
        '用感觉去行动吧', '别被自己情绪影响', '好好把握啦', '可按自己的目标进行计划', '转移目标吧', '多留意身边事物、另有出路', '凡事都有两面，一时不爽未必是坏事', '不妨改变一下想法', '重新想一下是否真正对你最重要吧',
        '记得不要太急进', '别再浪费时间', '辛苦的付出与收获不成正比，但切忌意气用事', '结果如何你都不会忘记这件事', '问题将会解决', '将会受到一些挫折，要积极面对', '有意外困扰，停滞不前，情绪会受到动摇', '不要心存侥幸，不付出又那会有收获呢',
        '出现了最佳时机，记着要踏实去干', '危机四伏，较为冲击动荡，需要过关斩将', '尝试去想一下其它更多的可能性', '迟一点才去解决', '不要自钻牛角尖，包容较挑剔来得开心', '小心外来的引诱，不要意气用事啊', '接受改变，面对现实啦', '困扰你的问题可望得到解决',
        '机会不会短期内再出现', '再想清楚你要的是什么', '等待一个更好机会', '你需要付出代价', '无论如何你都会继续去做', '你需要放弃其它东西才成事', '可能会好难，但值得的'
      ]
    }
  },
  onShow () {
  },
  methods: {
    getAns () {
      if (this.keywords === '改版') {
        this.entryShow = true
      } else {
        let date = new Date()
        let num = date.getSeconds()
        this.answer = this.ansList[num]
      }
    },
    goVersion1 () {
      wx.navigateTo({
        url: '/pages/headImg/main'
      })
    }
  },
  onHide () {
    this.answer = ''
    this.entryShow = false
  },
  onUnload () {
    this.answer = ''
    this.entryShow = false
  }
}
</script>

<style>
.container{
  background: linear-gradient(#13141B , #2E2043);
  width: 750rpx;
  height: 100vh;
  overflow-y: scroll;
  position: relative;
}
.input{
  color: #fff;
  font-size: 28rpx;
  width: 500rpx;
  text-align: center;
  margin: 250rpx 0 0 30rpx;
}
.askBtn{
  width: 150rpx;
  height: 70rpx;
  line-height: 70rpx;
  text-align: center;
  border-radius: 40rpx;
  color: #efefef;
  background: linear-gradient(#663366 , #6633FF);
  position: absolute;
  top: 240rpx;
  right: 50rpx;
}
.ansWrapper{
  position: absolute;
  bottom: 450rpx;
  left: 0;
}
.pha{
  width: 700rpx;
  color: #ffffff;
  font-size: 32rpx;
  font-weight: bold;
  margin-left: 25rpx;
  text-align: center;
}
.entryWrapper{
  position: absolute;
  bottom: 500rpx;
  left: 100rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 550rpx;
}
.entryBtn{
  width: 150rpx;
  height: 60rpx;
  line-height: 60rpx;
  text-align: center;
  background: linear-gradient(#6699FF , #FF99FF);
  margin: 0 20rpx;
  font-size: 30rpx;
  border-radius: 26rpx;
  color: #fff;
}
</style>
