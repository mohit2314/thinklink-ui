<template>
  <div class="dashboard__sidebar">
    <div
      v-for="(item, i) in sidebarMenuList"
      :class="['sidebar__list-item', { '--active': activeItem == i }]"
      :key="i"
      @click="activeItem = i"
    >
      <span><b-icon :icon="item.icon"></b-icon></span>
      <span>{{ item.label }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeItem: 0,
      sidebarMenuList: [
        {
          label: "Dashboard",
          icon: "command",
          // grid1x2
          // tv
        },
        {
          label: "Inventory",
          icon: "layers",
          // hdd-stack
          // intersect
          // stack
        },
        {
          label: "Orders",
          icon: "bag-check",
        },
        {
          label: "Customers",
          icon: "people",
        },
        {
          label: "Reports",
          icon: "file-text",
        },
        {
          label: "Settings",
          icon: "gear",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.dashboard__sidebar {
  width: 250px;
  height: 100vh;
  border-right: 1px solid #ecf1f4;
  .sidebar__list-item {
    cursor: pointer;
    padding: 12px;
    display: flex;
    gap: 16px;
    font-weight: 600;

    &.--active {
      color: #811434;
      background-color: #f7f1f3;
      box-shadow: 2px 0px 0px #811434;
    }
  }
}
</style>
