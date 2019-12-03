<template>
  <div class="container">
    <!-- <div class="userinfo" @click="bindViewTap">
      <img class="userinfo-avatar" src="/static/images/user.png" background-size="cover" />
      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
    </div> -->
    <!-- 个人信息区 -->
    <div class="userInfo flex">
      <div v-if="userInfo">
        <img class="avatar" :src="userInfo.avatarUrl"/>
        <p class="nickname">{{userInfo.nickName}}</p>
      </div>
      <button v-else class="getInfoBtn" open-type='getUserInfo' lang="zh_CN" @getuserinfo="onGotUserInfo">展示我的头像和昵称</button>
    </div>
    <!-- 功能区 -->
    <div class="activities flex">
      <div class="acItem flex" @click="goCounter">
        <img class="icon" src="/static/images/myPurchase.png"/>
        <span class="acName">冲鸭</span>
      </div>
      <div class="acItem flex" @click="goSky">
        <img class="icon" src="/static/images/redeem.png"/>
        <span class="acName">给你宇宙</span>
      </div>
      <div class="acItem flex" >
        <img class="icon" src="/static/images/myReport.png"/>
        <span class="acName">敬请期待</span>
      </div>
    </div>
    <!-- 推荐区 -->
    <div class="prepare">
      <div v-for="(item, index) in prepareList" :key="index" class="prepareItem"><span class="indexIcon">{{index + 1}}</span>{{item.name}}</div>
    </div>
  </div>
</template>

<script>
import card from '@/components/card'
export default {
  data () {
    return {
      userInfo: null,
      prepareList: [
        {type: 'book', name: '《山核桃大街谋杀案》'},
        {type: 'tv', name: '韩综——孝利家民宿'},
        {type: 'food', name: '热辣生活——麻辣去钳虾'},
        {type: 'food', name: '杨国福麻辣烫'},
        {type: 'food', name: '焦耳川式快餐——孜然豆角鸡'},
        {type: 'food', name: '李记桂林米粉螺蛳粉——螺蛳粉'}
      ]
    }
  },
  components: {
    card
  },
  methods: {
    onGotUserInfo (e) {
      console.log(JSON.parse(e.mp.detail.rawData))
      this.userInfo = JSON.parse(e.mp.detail.rawData)
    },
    bindViewTap () {
      const url = '../logs/main'
      if (mpvuePlatform === 'wx') {
        mpvue.switchTab({ url })
      } else {
        mpvue.navigateTo({ url })
      }
    },
    goCounter () {
      wx.navigateTo({
        url: '/pages/counter/main'
      })
    },
    goSky () {
      wx.navigateTo({
        url: '/pages/sky/main'
      })
    }
  },
  created () {}
}
</script>
<style>
button::after{ border: none; }
</style>

<style scoped>
.container{
  width: 750rpx;
  height: 100vh;
  overflow: scroll;
  -webkit-overflow-scrolling: touch;
  background: #F4F4F4;
}
/* 信息区 */
.userInfo{
  width: 750rpx;
  height: 300rpx;
  background: linear-gradient(#13141B , #2E2043);
  color: #ffffff;
}
.getInfoBtn{
  width: 650rpx;
  height: 80rpx;
  line-height: 80rpx;
  text-align: center;
  background: none;
  color: #ffffff;
  font-size: 32rpx;
}
.avatar{
  width: 80rpx;
  height: 80rpx;
  border-radius: 50%;
  float: left;
}
.nickname{
  width: 450rpx;
  height: 80rpx;
  line-height: 80rpx;
  margin-left: 50rpx;
  display: inline-block;
  overflow: hidden;
}
/* 功能区 */
.activities{
  width: 750rpx;
  height: 200rpx;
  /* background: #fff; */
}
.acItem{
  width: 200rpx;
  height: 200rpx;
  text-align: center;
  flex-direction: column;
}
.icon{
  width: 50rpx;
  height: 50rpx;
}
.acName{
  font-size: 28rpx;
}
/* 推荐区 */
.prepare{
  width: 700rpx;
  min-height: 200rpx;
  background: #fff;
  margin: 0 auto;
  border-radius: 20rpx;
}
.prepareItem{
  font-size: 32rpx;
  line-height: 100rpx;
}
.indexIcon{
  display: inline-block;
  width: 50rpx;
  height: 50rpx;
  line-height: 50rpx;
  border-radius: 50%;
  text-align: center;
  margin: 0 20rpx;
  color: #fff;
  font-weight: bold;
  font-size: 32rpx;
  background: #FA3B5F;
}
</style>
