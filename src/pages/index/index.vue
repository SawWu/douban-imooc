<template>
  <div class="container">
    <ul class="list">
      <li v-for="(card, index) in list" :key="index" class="item">
        <div></div>
        <span v-text="card.value"></span>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    data: () => ({
      list: [
        {
          value: '标题 8.9'
        },
        {
          value: '标题 8.9'
        },
        {
          value: '标题 8.9'
        },
        {
          value: '标题 8.9'
        }
      ]
    }),
    methods: {
      bindViewTap () {
        const url = '../logs/main'
        wx.navigateTo({url})
      },
      getUserInfo () {
        // 调用登录接口
        wx.login({
          success: () => {

          }
        })
      },
      clickHandle (msg, ev) {
        console.log('clickHandle:', msg, ev)
      }
    },

    created () {
      // 调用应用实例的方法获取全局数据
      this.getUserInfo()
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
    //overflow: hidden;

    & > div {
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
