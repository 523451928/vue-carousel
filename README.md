# vue-carousel
vue pc端:跑马灯 移动端:swiper

## 查看demo
```
git clone https://github.com/523451928/vue-carousel.git
cd vue-carousel
npm install
npm run dev
```
## vue-carousel 使用方法
```JavaScript

// ES6 mudule
import Carousel from './components/Carousel.vue'

```
注册 component:
```Javascript
Vue.component('Carousel',Carousel)
```

# 使用方法

```HTML
<carousel :imgArr="imgArr" clientType="mobile" duration="3000" ></carousel>
```

```JavaScript
export default {
    data() {
      return {
        imgArr: [
          '../static/bnr-1.jpg',
          '../static/bnr-3.jpg',
          '../static/bnr-4.jpg',
          '../static/bnr-5.jpg',
          '../static/bnr-2.jpg'
        ]
      }
    }
  }
```

# Options

Carousel props:

| props | Description |
| ----- | ----- |
| imgArr | Array(default: []) 图片数组 |
| hasDot | Boolean(default: true) 是否需要轮播图导航条 |
| triggerType | String(default: 'click') 导航条触发轮播的事件类型(click||hover) |
| clientType | String(default: 'pc') 需要运行在什么设备上(pc||mobile) |
| duration | Number(default: 3000) 多长时间播放一次 |
| isAuto | Boolean(defualt: true) 是否自动轮播 |
| isDrag | Boolean(default: true) 在pc端是否为可以拖拽 |
| distance | Number(default: 100) 拖拽或者touchend之后的距离触发跳至上一张或者下一张 |
