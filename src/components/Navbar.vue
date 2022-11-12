<template>
  <div class="app__navbar">
    <div class="nav__left-section">
      <div class="nav__brand-title">
        <img src="@/assets/brand-title.png" alt="" />
      </div>
      <div>
        <b-form-input
          size="sm"
          class="mr-sm-2 nav__search"
          placeholder="Search wines, customers here..."
        ></b-form-input>
      </div>
    </div>

    <div class="nav__right-section">
      <b-icon class="notification__icon" icon="bell" variant="light"></b-icon>

      <b-dropdown right variant="outlined">
        <!-- Using 'button-content' slot -->
        <template #button-content>
          <span class="user__name">Nicholas D.</span>
          <img src="@/assets/avtar.png" alt="" />
        </template>
        <b-dropdown-item href="#">Profile</b-dropdown-item>
        <b-dropdown-item href="#">Sign Out</b-dropdown-item>
      </b-dropdown>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
};
</script>
<style lang="scss">
.app__navbar {
  max-height: 56px;
  background-color: #811434;
  display: flex;
  width: 100%;
  padding: 8px 16px;
  align-items: center;
  font-size: 16px;
  color: #fff;
  .nav__left-section {
    width: 40%;
    display: flex;
    justify-content: space-between;
    .nav__search {
      width: 354px;
    }
  }
  .nav__right-section {
    display: flex;
    justify-content: flex-end;
    align-items: center;
    gap: 12px;
    width: 60%;
    .notification__icon {
      font-size: 18px;
    }
    .dropdown-toggle::after {
      color: #fff !important;
    }
    .user__name {
      color: #fff;
      margin-right: 12px;
    }
  }
}
</style>
