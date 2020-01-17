<template>
  <div class="tab-bar-item" @click="itemClick">
    <template v-if="!isActive">
      <slot name="item-icon"></slot>
    </template>
    <template v-else>
      <slot name="item-icon-active"></slot>
    </template>

    <div :style="activeStyle">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TabbarItem',
  props: {
    path: String,
    activecolor: {
      type: String,
      default: 'red'
    }
  },
  data() {
    return {

    }
  },
  computed: {
    isActive() {
      return this.$route.path.includes(this.path)
    },
    activeStyle() {
      return this.isActive ? { 'color': this.activecolor } : {}
    }
  },
  methods: {
    itemClick() {
      this.$router.replace(this.path).catch(err => {
        console.log(err,'all good')
      })
    }
  },
}
</script>

<style scpoe>
  .tab-bar-item {
    flex: 1;
    height: 49px;
    text-align: center;
  }
  .tab-bar-item img {
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
    margin-bottom: 2px;
  }
  .active {
    color: #ff0000
  }
</style>
