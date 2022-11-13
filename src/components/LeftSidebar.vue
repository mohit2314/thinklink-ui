<template>
  <div class="dashboard__sidebar">
    <div v-for="(item, i) in sidebarMenuList" :class="['sidebar__list-item', { '--active': activeItem == i }]" :key="i" @click="activeItem = i">
      <span><b-icon :icon="item.icon"></b-icon></span>
      <span>{{ item.label }}</span>
    </div>
    <div class="sidebar__footer">
      <div class="brand">CorkOwl</div>
      <div class="copyright-msg">© 2020 CorkOwl, All Rights Reserved.</div>
    </div>
    <div class="sidebar__collapse">
      <b-icon icon="arrow-left"></b-icon>
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
          label: 'Dashboard',
          icon: 'command',
          // grid1x2
          // tv
        },
        {
          label: 'Inventory',
          icon: 'layers',
          // hdd-stack
          // intersect
          // stack
        },
        {
          label: 'Orders',
          icon: 'bag-check',
        },
        {
          label: 'Customers',
          icon: 'people',
        },
        {
          label: 'Reports',
          icon: 'file-text',
        },
        {
          label: 'Settings',
          icon: 'gear',
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.dashboard__sidebar {
  width: 250px;
  // height: 100%;
  border-right: 1px solid #ecf1f4;
  // display: flex;
  // flex-direction: column;
  // justify-content: space-between;
  position: relative;
  .sidebar__list-item {
    min-width: 220px;

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
  .sidebar__footer {
    position: absolute;
    bottom: 42px;
    text-align: left;
    left: 24px;
    .brand {
      color: #8c8ca1;
      font-weight: 700;
    }
    .copyright-msg {
      font-weight: 400;
      font-size: 12px;
      line-height: 16px;
      /* identical to box height, or 133% */

      /* Subtle Text color */

      color: #8c8ca1;
    }
  }
  .sidebar__collapse {
    position: absolute;
    bottom: 46px;
    text-align: center;
    right: -10px;
    background-color: #ef4859;
    width: 20px;
    height: 20px;
    color: #fff;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
