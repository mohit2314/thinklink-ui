<template>
  <div class="app">
    <Navbar />
    <div class="dashboard__layout">
      <LeftSidebar class="sidebar__section" style="position: fixed; top: 56px; max-width: 250px; width: 350px; height: 100%" />
      <div class="dashboard__section">
        <DashboardSection style="margin-top: 60px" />
      </div>
    </div>
  </div>
</template>
<script>
import Navbar from '@/components/Navbar.vue';
import LeftSidebar from '@/components/LeftSidebar.vue';
import DashboardSection from '@/components/DashboardSection.vue';
export default {
  components: {
    Navbar,
    LeftSidebar,
    DashboardSection,
  },
};
</script>

<style lang="scss">
* {
  font-family: 'Open Sans';
  font-style: normal;
}
.app {
  width: 100%;
}
.dashboard__layout {
  display: flex;
  width: 100%;
  height: 100%;
  // background: #E5E5E5;
  width: 100%;
  .sidebar__section {
    width: 20%;
  }
  .dashboard__section {
    width: 100%;
    margin-left: 256px;
    display: flex;
    justify-content: center;
  }
}
</style>
