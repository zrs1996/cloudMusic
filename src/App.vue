<template>
  <div id="app">
    <music-header></music-header>
    <tab></tab>
    <keep-alive>
      <router-view></router-view>
    </keep-alive>
  </div>
</template>

<script>
import MusicHeader from 'components/music-header/music-header'
import Tab from 'components/tab/tab'
export default {
  name: 'App',
  components: {
    MusicHeader,
    Tab
  }
}
</script>

<style scope lang="stylus">
@import "~common/stylus/variable"
  .tab
    display flex
    height 44px
    line-height 44px
    width 100%
    font-size $font-size-medium
    background-color $color-theme
    .tab-item
      flex 1
      text-align center
      color $color-text-l
      span
        padding-bottom 3px
      &.router-link-active
        span
          font-weight bold
          color $color-text-l
          border-bottom 2px solid $color-text-l
</style>
