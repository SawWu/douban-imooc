<template>
  <div class="container">
    <ul class="list">
      <li v-for="(item, index) in list" :key="index" class="item">
        <img :src="item.cover" />
        <span v-text="item.title+'/'+item.rate"></span>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    data: () => ({
      list: []
    }),
    methods: {
      bindViewTap () {
        const url = '../logs/main'
        wx.navigateTo({url})
      },
      clickHandle (msg, ev) {
        console.log('clickHandle:', msg, ev)
      }
    },
    onLoad () {
      let that = this
      wx.request({
        url: `https://www.koocv.com/h5-view/v/movie/list`,
        header: {
          'content-type': 'application/json'
        },
        success (res) {
          that.list = res.data.subjects
        }
      })
    },
    created () {

    }
  }
</script>

<style lang="scss" scoped>
  .container {
    overflow: hidden;
  }

  .item {
    float: left;
    width: 335rpx;
    text-align: center;
    margin: 10rpx 20rpx;
    vertical-align: top;
    //overflow: hidden;

    & > img {
      width: 100%;
      height: 550rpx;
      box-shadow: 0 0 10px #ccc;
    }

    & > span {
      display: inline-block;
      width: 100%;
      font: 12px/1.5 "微润雅黑"
    }
  }
</style>
