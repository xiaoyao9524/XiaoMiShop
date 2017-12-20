<template>
    <div class="slider">
      <h1>Slider</h1>
      <ul class="nav">
        <li class="active">推荐</li><li>手机</li><li>全面屏</li><li>智能</li><li>电视</li><li>电脑</li><li>生活周边</li>
      </ul>
      <div class="page-wrap">
        <transition
          class="page-wrap"
          :name="outNum === index ? 'demo-right' : inNum === index ? 'demo-right' : ''"
          v-for="(item, index) in list" :key="index"
        >
          <div
            class="bodys"
            v-show="index === inNum"
          >{{item.title}}</div>
        </transition>
      </div>
      <button @click="togglePage">click</button>
    </div>
</template>

<script>
    export default {
      name: "slider",
      data () {
          return {
            list: [
              {
                title: 'a'
              },
              {
                title: 'b'
              },
              {
                title: 'c'
              }
            ],
            inNum: 0,
            outNum: 2
          }
      },
      methods: {
        togglePage () {
          this.inNum++
          if (this.inNum > (this.list.length - 1)) {
            this.inNum = 0
          }
          this.outNum++
          if (this.outNum > (this.list.length - 1)) {
            this.outNum = 0
          }
        }
      }
    }
</script>

<style scoped>
  .nav {
    overflow-x: auto;
    overflow-y: hidden;
    white-space: nowrap;
  }
  .nav::-webkit-scrollbar {
    height: 0;
    background:transparent;
  }
  .nav li {
    display: inline-block;
    padding: 3px 20px;
    border-bottom: 2px solid #fff;
  }
  .nav li.active {
    color: rgb(237, 91, 0);
    border-bottom: 2px solid rgb(237, 91, 0);
  }
  .page-wrap {
    position: relative;
    /*overflow-x: auto;*/
    /*overflow-y: hidden;*/
    overflow: hidden;
    white-space: nowrap;
    height: 400px;
  }
  .page-wrap::-webkit-scrollbar {
    height: 0;
  }
  .bodys {
    position: absolute;
    top: 0;
    left: 0;
    width: 414px;
    height: 400px;
  }
  .bodys:nth-of-type(1) {
    background: pink;
  }
  .bodys:nth-of-type(2) {
    background: palegreen;
  }
  .bodys:nth-of-type(3) {
    background: paleturquoise;
  }
  .demo-left {
    left: 0;
  }
  .demo-left-enter-active, .demo-left-leave-active, .demo-right-enter-active, .demo-right-leave-active {
    transition: 10s;
  }
  .demo-left-enter, .demo-left-leave-to {
    left: 0;
  }
  .demo-left-enter-to, .demo-left-leave {
    left: -400px;
  }
  .demo-right {
    left: 0;
  }
  .demo-right-enter {
    left: 400px;
  }
  .demo-right-leave-to {
    left: -400px;
  }
  .demo-right-enter-to, .demo-right-leave {
    left: 0;
  }
</style>
