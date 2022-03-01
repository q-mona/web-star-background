# web-star-background
 用canvas绘制的网页版星星背景
# 预览
![](https://raw.githubusercontent.com/q-mona/mona/master/preview.gif)
# 使用说明
详细请看index.html
```
// 配置信息
const cfg = {
    "star": {
        "min_size": 10, // 最小尺寸
        "max_size": 40, // 最大尺寸
        "rot": 0,  // 随机初始旋转角度(0则不旋转)
        "rot_step": 0, // 每帧旋转角度(0则不旋转) 由于是五角星 建议此处为9的倍数(0 9 18 36)
        "min_step": 0.5, // 每间隔移动最小距离
        "max_step": 2, // 每间隔移动最大距离
        "num": 20 // 星星数量
    },
    "moon": {
        "min_size": 10, // 最小尺寸
        "max_size": 40, // 最大尺寸
        "rot": 360, // 随机初始旋转角度(0-360)
        "rot_step": 0, // 每帧旋转角度(0则不旋转)
        "min_step": 0.5, // 每间隔移动最小距离
        "max_step": 2, // 每间隔移动最大距离
        "num": 20 //月亮数量
    },
    "canvas": {
        "width": window.innerWidth, // 画布宽
        "height": window.innerHeight, // 画布高
        "interval": 40, // 动画间隔(ms)
        "globalAlpha": 0.6, // 画布透明度
        "direction": "down", // 方向(up down left right)
        // 生成星星的范围(画布左上为远点 xy为宽长宽的矩形)
        "x": window.innerWidth, 
        "y": 400,
    }
}

// 初始化
loadStar(el_star_img, el_moon_img, cfg)
// el_star_img、el_moon_img为星星、月亮图片，可自定义
// cfg为上方的配置信息
```  

在vue3中使用  
由于直接在index.html引入图片打包后路径可能有误，因此建议在.vue文件中初始化并记得在star.js中export loadStar。
```
<script setup>
import loadStar from '@/js/star.js'
import star from '@/images/star.png' // 导入assets的图片
import moon from '@/images/moon.png'

const cfg = {
  "star": {
    "min_size": 10,
    "max_size": 30,
    "rot": 360,
    "rot_step": 0,
    "min_step": 1,
    "max_step": 4,
    "num": 15
  },
  "moon": {
    "min_size": 10,
    "max_size": 30,
    "rot": 360,
    "rot_step": 0,
    "min_step": 1,
    "max_step": 4,
    "num": 15
  },
  "canvas": {
    "width": window.innerWidth,
    "height": window.innerHeight,
    "interval": 60,
    "globalAlpha": 0.6,
    "direction": "down",
    "x": window.innerWidth,
    "y": 300,
  }
}
const el_star_img = document.createElement('img')
el_star_img.src = star
const el_moon_img = document.createElement('img')
el_moon_img.src = moon

loadStar(el_star_img, el_moon_img, cfg)
</script>

<template>
</template>

<style scoped>
</style>
```
