<template>
  <div id="main-box">
    <div id="content-box">
      <Header />
      <div class="app-main">
        <router-view />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import Header from "./header.vue";
</script>

<style lang="less">
#main-box {
  width: 100%;
  display: flex;

  #content-box {
    flex: 1;

    .app-main {
      width: 100%;
      height: calc(100vh - 64px);
      padding: 15px;
      box-sizing: border-box;
      background-color: rgba(0, 0, 0, 0.1);
    }
  }
}
</style>
