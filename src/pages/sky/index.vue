<template>
  <div class="container" @click="getItem">
    <span class="add" v-for="(el, index) in starList" :key="index" :style="{left: el.x, top: el.y, opacity: el.r, fontWeight: el.r*80+'rpx'}">·</span>
    <img class="bg-img" src="/static/images/sky-bg.png"/>
  </div>
</template>

<script>
export default {
  data () {
    return {
      starList: []
    }
  },
  components: {},
  methods: {
    getItem (e) {
      if (this.starList.length >= 15) {
        this.starList.shift()
      }
      let opNum = Math.random()
      this.starList.push({x: e.clientX + 'px', y: e.clientY + 'px', r: opNum})
    }
  },
  created () {}
}
</script>

<style scoped>
.container{
  width: 750rpx;
  height: 100vh;
  position: relative;
}
.bg-img{
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}
.add{
  color: #fff;
  position: absolute;
  z-index: 2;
}
</style>