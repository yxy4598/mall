<template>
    <div class="tab-bar-item" @click="btnClick">
      <slot v-if="!isActive" name="item-icon"></slot>
      <slot v-else name="item-icon-active"></slot>
      <div :style="activeStyle"><slot name="item-text"></slot></div>
    </div>
</template>

<script>
    export default {
      name: "TabBarItem",
      props: {
        path: String,
        activeColor: {
          type: String,
          default: 'red'
        }
      },
      data() {
        return {
          // isActive: true
        }
      },
      //计算属性
      computed: {
        isActive() {
          return this.$route.path.indexOf(this.path) !== -1
        },
        activeStyle() {
          return this.isActive ? {color: this.activeColor} : {}
        }
      },
      methods: {
        btnClick() {
          this.$router.push(this.path)
        }
      }
    }
</script>

<style scoped>
  .tab-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
    color:black;
  }

  .tab-bar-item img {
    width: 24px;
    height: 24px;
    vertical-align: middle;
    margin: 4px 0 2px 0;
  }

  .actived {
    color:coral;
    font-weight: bolder;
  }
</style>
