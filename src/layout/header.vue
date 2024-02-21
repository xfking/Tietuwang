<template>
  <div class="nav-header"></div>
</template>

<script setup lang="ts">
import { computed } from "vue";
import { useRouter } from "vue-router";
import { appStore } from "@/store/index";
import { userStore } from "@/store/user";
const store = appStore();
const users = userStore();
const router = useRouter();
const collapsed = computed(() => store.$state.collapsed);
const options = [
  {
    content: "返回首页",
    value: 1,
  },
  {
    content: "登出",
    value: 2,
  },
];
const changeCollapsed = () => {
  store.changeCollapsed(!collapsed.value);
};
const handleClick = (data: any) => {
  const { value } = data;
  switch (value) {
    case 1:
      router.push({ path: "/" });
      break;
    case 2:
      users.logout().then(() => {
        router.push({ path: "/" });
        location.reload();
      });
      break;
  }
};
</script>

<style lang="less">
.nav-header {
  width: 100%;
  height: 64px;
  color: #fff;
}

.t-menu__logo > * {
  margin-left: 24px;
}

.t-head-menu__inner .t-menu:first-child {
  margin-left: 0 !important;
}
</style>
