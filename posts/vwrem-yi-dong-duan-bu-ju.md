---
title: 'vw+rem 移动端布局'
date: 2020-01-14 09:39:04
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
[网易新闻移动端布局](https://static.ws.126.net/163/wap/f2e/milk-channel/common.a68191b4.css)
```css
/**
 * view-port list:
320x480
320x568
320x570
360x592
360x598
360x604
360x640
360x720
375x667
375x812
393x699
412x732
414x736
480x854
540x960
640x360
720x1184
720x1280
800x600
1024x768
1080x1812
1080x1920
 */
html {
  font-size: -webkit-calc(13.33333333vw);
  font-size: calc(13.33333333vw);
}
@media screen and (max-width: 320px) {
  html {
    font-size: 42.667px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 321px) and (max-width: 360px) {
  html {
    font-size: 48px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 361px) and (max-width: 375px) {
  html {
    font-size: 50px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 376px) and (max-width: 393px) {
  html {
    font-size: 52.4px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 394px) and (max-width: 412px) {
  html {
    font-size: 54.93px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 413px) and (max-width: 414px) {
  html {
    font-size: 55.2px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 415px) and (max-width: 480px) {
  html {
    font-size: 64px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 481px) and (max-width: 540px) {
  html {
    font-size: 72px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 541px) and (max-width: 640px) {
  html {
    font-size: 85.33px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 641px) and (max-width: 720px) {
  html {
    font-size: 96px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 721px) and (max-width: 768px) {
  html {
    font-size: 102.4px;
    font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw);
  }
}
@media screen and (min-width: 769px) {
  html {
    font-size: 102.4px;
    /* font-size: -webkit-calc(13.33333333vw);
    font-size: calc(13.33333333vw); */
  }
}
```