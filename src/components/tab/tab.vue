<template>
  <div class="tab">
      <router-link tag="div" class="tab-item" to="/recommend">
        <span>推荐</span>
      </router-link>
      <router-link tag="div" class="tab-item" to="/rank">
        <span>排行</span>
      </router-link>
      <router-link tag="div" class="tab-item" to="/singer">
        <span>歌手</span>
      </router-link>
  </div>
</template>

<script>
export default {
    name: "tab"
}
</script>

<style>

</style>