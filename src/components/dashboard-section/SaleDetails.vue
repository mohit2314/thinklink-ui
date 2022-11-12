<template>
  <div class="sale__details-section">
    <div class="section__heading-row">Sales Details</div>
    <div class="sales__card">
      <div class="sales__card-header">
        <div class="left__section">
          <span style="color: #262730; font-size: 16px">Total Sales Overview</span>
          <span style="color: #868686; font-size: 14px">7 - 13 Aug, 2020</span>
        </div>
        <div class="right__section">
          <span style="color: #485572; font-size: 14px; font-weight: 600; margin-right: 32px"><b-icon icon="arrow-repeat"></b-icon> Refresh Metrics</span>
          <span style="font-weight: 700; font-size: 16px; line-height: 24px; text-align: right; color: #8c8ca1">Filter by </span>
          |
          <span style="color: #262730; font-size: 16px; font-weight: 700">This week <b-icon icon="chevron-down"></b-icon></span>
        </div>
      </div>
      <!-- Sales card main section -->
      <div class="sales__card-main-section">
        <!-- Left section -->
        <div class="left__section">
          <div class="graph__data-row">
            <span style="color: #262730; font-size: 48px"> $74,729.00</span>
            <span class="d-flex align-items-center" style="font-size: 16px; font-weight: 600">
              <span><b-icon style="color: #2fca72; margin-right: 8px" icon="graph-up"></b-icon></span>
              <span style="color: #262730">Highest revenue since 2 weeks ago</span>
            </span>
          </div>
          <div class="graph__data-row">
            <span style="color: #2fca72; font-size: 16px; font-weight: 600"><b-icon icon="graph-up"></b-icon> +21% from last week</span>
          </div>
          <!-- Graph row -->
          <div class="graph__row">
            <img src="@/assets/Graph.png" alt="" />
          </div>
        </div>
        <div class="right__section">
          <div class="profit__summary">
            <div class="headings">Total Profit</div>
            <div style="color: #811434; font-size: 32px; font-weight: 700">$12,545.00</div>
            <div style="color: #2fca72; font-size: 16px; font-weight: 600"><b-icon icon="graph-up"></b-icon> +23% from last week</div>
          </div>
          <div class="sales__summary">
            <div class="headings">Total Products Sold</div>
            <div style="color: #262730; font-size: 32px">329</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.section__heading-row {
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  /* identical to box height, or 150% */

  /* Dark color */

  color: #262730;
  margin: 24px 0 16px 0;
}
.sales__card {
  border: 1px solid #fff2ee;
  border-radius: 4px;
  width: 1122px;
  .sales__card-header {
    display: flex;
    justify-content: space-between;
    border-bottom: 1px solid #fff2ee;
    padding: 16px;
    .left__section {
      display: flex;
      flex-direction: column;
      //   gap: 8px;
    }
  }
  .sales__card-main-section {
    display: flex;
    .left__section {
      width: 70%;
      padding: 20px;
      border-right: 1px solid #fff2ee;
      .graph__data-row {
        display: flex;
        justify-content: space-between;
        align-items: center;
      }
      .graph__row {
        width: 100%;
        height: 100%;
        object-fit: cover;
        overflow: hidden;
      }
    }
    .right__section {
      width: 30%;
      display: flex;
      flex-direction: column;
      gap: 40px;
      padding: 20px;
      .headings {
        color: #8c8ca1;
        font-size: 16px;
        font-weight: 700;
      }
      .profit__summary {
      }
    }
  }
}
</style>
