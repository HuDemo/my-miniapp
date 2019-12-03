<template>
  <div class="counter-warp">
    <p>冲啊：{{ count }}只头不动鸡正在奔跑起来</p>
    <p>
      <button class="counter-btn" @click="increment">+</button>
      <button class="counter-btn" @click="decrement">-</button>
    </p>
    <div class="img-container" v-if="count > 0">
      <div class="img-item" v-for="(item, index) in count" :key="index">
        <img v-if="(count <= 50)" class="go-running" :class="(count > 18)? 'mini-running':''" src="/static/images/go-running.png" alt=""/>
        <img v-else class="go-running small-running" src="/static/images/go-running.png" alt=""/>
      </div>
    </div>
  </div>
</template>

<script>
// Use Vuex
import store from './store'

export default {
  computed: {
    count () {
      return store.state.count
    }
  },
  methods: {
    increment () {
      store.commit('increment')
    },
    decrement () {
      store.commit('decrement')
    }
  }
}
</script>

<style>
button::after{
  border: none;
}
.counter-warp {
  text-align: center;
  margin-top: 50rpx;
  font-size: 32rpx;
  color: #1f6fb5;
  font-weight: bold;
}
.counter-btn{
  display: inline-block;
  width: 300rpx;
  height: 80rpx;
  line-height: 80rpx;
  border: none;
  border-radius: 20rpx;
  background: #9dd3fa;
  color: #faffeb;
  margin: 10rpx;
}
.img-container{
  text-align: left;
}
.img-item{
  display: inline-block;
}
.go-running{
  width: 250rpx;
  height: 175rpx;
  vertical-align: middle;
}
.mini-running{
  width: 150rpx;
  height: 105rpx;
}
.small-running{
  width: 75rpx;
  height: 52.5rpx;
}
</style>
