<template>
  <div>
    <Navbar />
    <div class="dashboard__layout">
      <LeftSidebar />
      <DashboardSection />
    </div>
  </div>
</template>
<script>
import Navbar from "@/components/Navbar.vue";
import LeftSidebar from "@/components/LeftSidebar.vue";
import DashboardSection from "@/components/DashboardSection.vue";
export default {
  components: {
    Navbar,
    LeftSidebar,
    DashboardSection,
  },
};
</script>

<style lang="scss">
.dashboard__layout {
  display: flex;
  width: 100%;
}
</style>
