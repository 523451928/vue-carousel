<template>
  <div class="layer1">
    <div class="layer2">
      <ul class="content text-center walllife">
        <transition-group name="fade">
          <li v-for="(item, index) in bannerData" v-show="activeId===index" class="list" :key="index">
            <img :src="item" class="item"/>
          </li>
        </transition-group>
        <ol class="carousel-indicators" v-if="hasDot">
          <li v-for="(item,index) in bannerData" :class="{'active':index===activeId}"
              @click="changeBanner(index)" @mouseenter="changeBanner(index)"></li>
        </ol>
        <a href="javascript:void(0)" class="carousel-control left" @click="prev" @mouseleave="autoPlay"></a>
        <a href="javascript:void(0)" class="carousel-control right" @click ="next" @mouseleave="autoPlay"></a>
      </ul>
    </div>
  </div>
</template>

<script>
  export default{
    props: {
      bannerData: {
        type: Array,
        default() {
          return []
        }
      },
      duration: {
        type: Number,
        default: 5000
      },
      hasDot: {
        type: Boolean,
        default: true
      },
      triggerType: {
        type: String,
        default: 'hover'
      }
    },
    data() {
      return {
        activeId: 0,
        interval: null
      }
    },
    methods: {
      autoPlay() {
        if (this.interval) {
          this.stopInterval()
        }
        this.interval = setInterval(() => {
          this.prev()
        }, this.duration)
      },
      prev() {
        this.activeId --
        if (this.activeId < 0) {
          this.activeId = this.bannerData.length - 1
        }
        this.stopInterval()
      },
      stopInterval() {
        clearInterval(this.interval)
      },
      next() {
        this.activeId ++
        if (this.activeId > this.bannerData.length - 1) {
          this.activeId = 0
        }
        this.stopInterval()
      },
      changeBanner(idx) {
        if (this.triggerType === 'click') {
          this.activeId = idx
        }
        if (this.triggerType === 'hover') {
          this.activeId = idx
        }
      }
    }
  }
</script>

<style lang="scss">
  .fade-enter-active, .fade-leave-active {
    transition: all .5s;
  }
  .fade-enter,.fade-leave-to /* .fade-leave-active in below version 2.1.8 */ {
    opacity: 0;
  }
  .walllife-bg {
    height: 100%;
    background-size: cover;
  }
  .layer1, .layer2 {
    width: 100%;
    height: 300px;
    position: relative;
    margin-top: 30px;
  }
  .layer2 {
    left: 0;
    z-index: 99;
    .content {
      height:100%;
      position:relative;
      &:hover {
        .carousel-control {
          display: block;
        }
      }
      .list {
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        background-repeat: no-repeat;
        background-size: cover;
        background-position: 50%;
        overflow: hidden;
        .item {
          width:100%;
        }
      }
      .carousel-control {
        display:none;
        &:hover {
          opacity:1
        }
        &.left {
          background-image: none;
          position: absolute;
          left: 0;
          width:100px;
          height: 100%;
          display: block;
          &:after {
            content: " ";
            position: absolute;
            display: inline-block;
            -webkit-transform: rotate(-135deg);
            -ms-transform: rotate(-135deg);
            transform: rotate(-135deg);
            height: 40px;
            width: 40px;
            border-width: 2px 2px 0 0;
            border-color: #888;
            border-style: solid;
            top: 50%;
            left: 30%;
          }
        }
        &.right {
          background-image: none;
          position: absolute;
          right: 0;
          width:100px;
          height: 100%;
          display: block;
          &:after {
            content: " ";
            position: absolute;
            display: inline-block;
            height: 40px;
            width: 40px;
            border-width: 2px 2px 0 0;
            border-color: #888;
            border-style: solid;
            -webkit-transform: rotate(45deg);
            -ms-transform: rotate(45deg);
            transform: rotate(45deg);
            top: 50%;
            left: 0%;
          }
        }
      }
      .carousel-indicators {
        bottom: 17px;
        margin-left: -34px;
        height: 12px;
        width: 30%;
        position: absolute;
        left: 50%;
        li {
          margin-right: 16px;
          border: none;
          background-color: #999;
          border-radius: 50%;
          box-sizing: border-box;
          list-style: none;
          width: 12px;
          height:12px;
          float: left;
          &.active {
            width: 12px;
            height: 12px;
            background: none;
            border: 1px solid #26a7c7;
          }
        }
      }
      .carousel-control {
        background-image: none;
      }
    }
  }
  .weui_tab{
    position: relative;
    height: 100%;
  }
  .walllife {
    .row-text {
      position: absolute;
      top: 50%;
      left: 50%;
      min-width: 300px;
      width: 100%;
      -webkit-transform: translate(-50%,-50%);
      transform: translate(-50%,-50%);
    }
    img{
      height: 100%;
    }
    h1 {
      &.active {
        color:#565a5c;
      }
    }
    span {
      display: block;
      font-size: 20px;
      color: #fff;
      line-height: 1.5;
      &.active {
        color:#565a5c;
      }
    }
  }
  .row-text .btn-detail {
    background: none;
    border: 1px solid #26a7c7;
    color: #26a7c7;
    padding: 13px 48px;
    margin-bottom: 10px;
  }

  .walllife .open:hover {
    background: #26a7c7;
    color: #fff;
    border: 1px solid #26a7c7;
  }
</style>
