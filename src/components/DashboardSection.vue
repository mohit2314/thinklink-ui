<template>
  <b-container class="dashboard__container">
    <!-- Header row -->
    <b-row>
      <div class="dashboard__header-row">
        <span class="header__title">Overview</span>
        <span
          ><b-button class="header__cta-btn"
            ><b-icon class="plus-icon" icon="plus-circle"></b-icon> ADD NEW
            WINE</b-button
          ></span
        >
      </div>
    </b-row>
  </b-container>
</template>

<script>
export default {
  components: {},
};
</script>

<style lang="scss">
.dashboard__container {
  padding: 16px;
}
.dashboard__header-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 700;
  width: 100%;

  .header__title {
    font-size: 20px;
    color: #8c8ca1;
  }
  .header__cta-btn {
    background-color: #ef4859;
    color: #fff;
    outline: none;
    border: none;
    font-size: 14px;
    font-weight: 600;
    padding: 8px 20px;
    border-radius: 4px;
    max-width: 182px;
    .plus-icon {
      margin-right: 8px;
    }
  }
}
</style>
