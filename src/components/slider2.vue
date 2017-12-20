<template>
  <div class="slider">
    <h1>小米商城</h1>
    <ul class="nav">
      <li
        v-for="(item, index) in list"
        :class="{active: index === inNum}"
        @click="tabPage(index)"
        :key="index"
      >
      {{item.title}}
      </li>
    </ul>

    <div class="page-wrap">
      <transition
        class="page-wrap"
        v-for="(item, index) in list"
        :key="index"
        :name="inNum === index ? outNum > index ? 'left-in' : 'right-in' : outNum === index ? outNum > inNum ? 'right-out' : 'left-out' : ''"
      >
        <bodys 
          class="bodys"
          v-show="index === inNum"
          :list="item"
        >
        </bodys>
      </transition>
    </div>
  </div>
</template>

<script>
  import bodys from './bodys'
    export default {
      name: "slider",
      data () {
          return {
            list: [
              {
                title: '推荐'
              },
              {
                title: '手机'
              },
              {
                title: '全面屏'
              },
              {
                title: '智能'
              },
              {
                title: '电视'
              },
              {
                title: '电脑'
              },
              {
                title: '生活周边'
              }
            ],
            inNum: 0,
            outNum: 0
          }
      },
      components: {
        bodys
      },
      methods: {
        tabPage (index) {
          this.outNum = this.inNum;
          this.inNum = index;
          // let _this = this;
          // setTimeout(function () {
          //   _this.outNum = _this.inNum;
          //   _this.inNum = index;
          // }, 1000) // 模拟延迟
        }
      }
    }
</script>

<style scoped>
  h1 {
    text-align: center;
  }
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
    overflow: hidden;
    white-space: nowrap;
    height: 400px;
  }
  .page-wrap::-webkit-scrollbar {
    height: 0;
  }
  /* demo start */
  .left-in-enter-active,
  .left-in-leave-active,
  .left-out-enter-active,
  .left-out-leave-active,
  .right-in-enter-active,
  .right-in-leave-active,
  .right-out-enter-active,
  .right-out-leave-active { /*时间*/
    transition: .3s;
  }
  .left-in-enter, .left-in-leave-to {/*左侧进入 start*/
    transform: translate(-400px, 0);
  }
  .left-in-enter-to, .left-in-leave {/*左侧进入 end*/
    transform: translate(0, 0);
  }
  .left-out-leave, .left-out-enter-to {/*左侧出去 start*/
    transform: translate(0, 0);
  }
  .left-out-leave-to, .left-out-enter {/*左侧出去 end*/
    transform: translate(-400px, 0);
  }
  .right-in-enter, .right-in-leave-to {
    transform: translate(400px, 0);
  }
  .right-in-enter-to, .right-in-leave {
    transform: translate(0, 0);
  }
  .right-out-enter, .right-out-leave-to {
    transform: translate(400px, 0);
  }
  .right-out-enter-to, .right-out-leave {
    transform: translate(0, 0);
  }
</style>
