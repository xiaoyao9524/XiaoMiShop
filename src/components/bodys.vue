<template>
    <div class="bodys">
      {{list.title}}
    </div>
</template>

<script>
  export default {
    name: "bodys",
    props: {
      list: {
        default: {},
        type: Object
      }
    },
    methods: {
    }
  }
</script>

<style scoped>
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
</style>
