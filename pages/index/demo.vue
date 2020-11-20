<template>
  <view>
    <view id="bg" ref="bg" :style="bgStyle" class="animation" />
  </view>
</template>

<script>
  export default {
    data() {
      return {
        bgStyle: {
          width: null,
          '--x-offset': null
        },
        // 图片的尺寸
        image: {
          width: 200,
          height: 280
        }
      }
    },
    created() {
      const fun = () => {
        const clientHeight = document.body.clientHeight | (document.documentElement && document.documentElement
          .clientHeight)
        const xOffset = parseInt(this.image.width / this.image.height * clientHeight)
        this.bgStyle['--x-offset'] = xOffset + 'px'
        this.bgStyle.width = document.body.clientWidth + xOffset + 'px'
      }
      window.onresize = () => {
        fun()
        // 重置 animation 保证动画刷新
        this.$refs.bg.classList.remove('animation')
        setTimeout(() => {
          this.$refs.bg.classList.add('animation')
        }, 100)
      }
      fun()
    }
  }
</script>

<style lang='scss'>
  /* 需要污染到全局的 css ，防止带上 hash 影响操作 */

  @keyframes bg {
    0% {
      transform: translateX(0);
    }

    100% {
      transform: translateX(calc(-1 * var(--x-offset)));
    }
  }

  .animation {
    animation: bg 13s linear infinite;
  }
</style>

<style scoped lang='scss'>
  /* 背景图像的节点 */

  #bg {
    background: url(../../static/imgs/double11/single/min1.png) top left;
    background-repeat: repeat-x;
    background-size: var(--x-offset) auto, auto;
    height: 100%;
    position: fixed;
    left: 0;
    top: 0;
  }
</style>