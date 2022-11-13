<template>
  <b-container class="dashboard__container">
    <!-- Header row -->
    <b-row class="mb-4">
      <div class="dashboard__header-row">
        <div class="header__title">Overview</div>
        <div>
          <b-button class="header__cta-btn"><b-icon class="plus-icon" icon="plus-circle"></b-icon> ADD NEW WINE</b-button>
        </div>
      </div>
    </b-row>
    <!-- Status Card row -->
    <b-row>
      <div class="status__card-row">
        <StatusCard v-for="(card, i) in statusCardList" :key="i" :card="card" />
      </div>
    </b-row>
    <!-- Sales details Section -->
    <b-row>
      <div>
        <SaleDetails />
      </div>
    </b-row>
    <!-- Inventory Section -->
    <b-row>
      <div>
        <InventorySection />
      </div>
    </b-row>
  </b-container>
</template>

<script>
import StatusCard from './dashboard-section/StatusCard.vue';
import SaleDetails from './dashboard-section/SaleDetails.vue';
import InventorySection from './dashboard-section/InventorySection.vue';
export default {
  components: {
    StatusCard,
    SaleDetails,
    InventorySection,
  },
  data() {
    return {
      statusCardList: [
        {
          title: 'Open orders',
          icon: 'basket2',
          value: 239,
          color: '#ffbf61',
        },
        {
          title: 'Orders in transit',
          icon: 'truck',
          value: 126,
          color: '#618dFF',
        },
        {
          title: 'Fulfilled orders',
          icon: 'bag-check',
          value: '1,254',
          color: '#40db6b',
        },
        {
          title: 'Cancelled orders',
          icon: 'x-circle',
          value: 35,
          color: `#FF5555`,
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.dashboard__container {
  padding: 24px 34px;
  // display: flex;
  // flex-direction: column;
  // justify-content: center;
  // align-items: center;
  max-width: 1220px !important;
}
.dashboard__header-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 700;
  max-width: 920px;

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
    margin-right: 80px;
    .plus-icon {
      margin-right: 8px;
    }
  }
}
.status__card-row {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  gap: 30px;
}
</style>
