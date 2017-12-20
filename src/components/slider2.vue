<template>
    <div class="slider">
      <h1>小米商城</h1>
      <ul class="nav">
        <li
          v-for="(item, index) in list"
          :class="{active: index === inNum}"
          @click="tabPage(index)"
        >{{item.title}}
        </li>
      </ul>
      <div class="page-wrap">
        <transition
          class="page-wrap"
          v-for="(item, index) in list"
          :key="index"
          :name="inNum === index ? outNum > index ? 'left-in' : 'right-in' : outNum === index ? outNum > inNum ? 'right-out' : 'left-out' : ''"
        >
          <!--
            将要进入的是这个元素吗？
              是的话：将要出去的元素比他大吗？
                大的话：从左边进('left-in')
                小的话：从右边进('right-in')
              不是的话：要出去的是这个元素吗？
                是的话：要出去的元素（就是这个元素）比进入的元素大吗？
                  大的话： 从右边出去('right-out')
                  小的话： 从左边出去('left-out')
            如果出去进来都不是这个元素
              什么都不做 ('')
          -->
          <div
            class="bodys"
            v-show="index === inNum"
          >{{item.title}}
          </div>
        </transition>
      </div>
    </div>
</template>

<script>
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
      computed: {
      },
      methods: {
        tabPage (index) {
          // this.outNum = this.inNum;
          // this.inNum = index;
          let _this = this;
          setTimeout(function () {
            _this.outNum = _this.inNum;
            _this.inNum = index;
          }, 1000) // 模拟延迟
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
  .bodys {
    position: absolute;
    top: 0;
    left: 0;
    width: 414px;
    height: 400px;
    border: 1px solid #000;
    box-sizing: border-box;
    background: paleturquoise;
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
    left: -400px;
  }
  .left-in-enter-to, .left-in-leave {/*左侧进入 end*/
    left: 0;
  }
  .left-out-leave, .left-out-enter-to {/*左侧出去 start*/
    left: 0;
  }
  .left-out-leave-to, .left-out-enter {/*左侧出去 end*/
    left: -400px;
  }
  .right-in-enter, .right-in-leave-to {
    left: 400px;
  }
  .right-in-enter-to, .right-in-leave {
    left: 0;
  }
  .right-out-enter, .right-out-leave-to {
    left: 400px;
  }
  .right-out-enter-to, .right-out-leave {
    left: 0;
  }
</style>
