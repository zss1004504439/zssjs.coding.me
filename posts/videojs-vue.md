---
title: 'videojs-vue'
date: 2019-11-04 18:30:52
tags: [video]
published: true
hideInList: false
feature: 
---
## videojs 使用
### 安装 npm 包
#### vue-video-player
#### videojs-contrib-hls
### main.js 引用
### 查看 videojs api
```html
<template>
  <section class="demo">
    <video-player
      ref="videoPlayer"
      class="video-player vjs-custom-skin"
      :playsinline="true"
      :options="playerOptions"
      @play="onPlayerPlay($event)"
      @pause="onPlayerPause($event)"
    />
  </section>
</template>

<script>
// vue-video-player
// import VideoPlayer from 'vue-video-player'
// require('video.js/dist/video-js.css')
// require('vue-video-player/src/custom-theme.css')
// const hls = require('videojs-contrib-hls')
// Vue.use(hls)
// Vue.use(VideoPlayer)
// vue-video-player end
export default {
  name: 'Demo',
  components: { },
  data() {
    return {
      playerOptions: {
        // playbackRates: [0.7, 1.0, 1.5, 2.0], //播放速度
        autoplay: false, // 如果true,浏览器准备好时开始回放。
        muted: false, // 默认情况下将会消除任何音频。
        loop: false, // 导致视频一结束就重新开始。
        preload: 'auto', // 建议浏览器在<video>加载元素后是否应该开始下载视频数据。auto浏览器选择最佳行为,立即开始加载视频（如果浏览器支持）
        language: 'zh-CN',
        aspectRatio: '16:9', // 将播放器置于流畅模式，并在计算播放器的动态大小时使用该值。值应该代表一个比例 - 用冒号分隔的两个数字（例如"16:9"或"4:3"）
        fluid: true, // 当true时，Video.js player将拥有流体大小。换句话说，它将按比例缩放以适应其容器。
        sources: [
          {
            type: 'application/x-mpegURL', // 这里的种类支持很多种：基本视频格式、直播、流媒体等，具体可以参看git网址项目
            src:
              'https://node.imgio.in/demo/birds.m3u8' // url地址，从别的博主那看来的地址，亲测可用
          }
          // {
          //   type: 'video/mp4', // 这里的种类支持很多种：基本视频格式、直播、流媒体等，具体可以参看git网址项目
          //   src: 'https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm' // url地址
          // }
        ],
        hls: true,
        poster: 'http://pic33.nipic.com/20131007/13639685_123501617185_2.jpg', // 你的封面地址
        width: document.documentElement.clientWidth, // 播放器宽度
        notSupportedMessage: '此视频暂无法播放，请稍后再试', // 允许覆盖Video.js无法播放媒体源时显示的默认信息。
        controlBar: {
          timeDivider: true,
          durationDisplay: true,
          remainingTimeDisplay: false,
          fullscreenToggle: true // 全屏按钮
        }
      }
    }
  },
  computed: {
    player() {
      return this.$refs.videoPlayer.player// 自定义播放
    }
  },
  watch: {},
  mounted() {},
  methods: {
    onPlayerPlay() {

    },
    onPlayerPause() {

    }
  }
}
</script>

<style scoped  >

</style>

```
[参考](https://segmentfault.com/a/1190000020149370)