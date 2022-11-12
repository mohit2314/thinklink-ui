<template>
  <div
    class="status__card"
    :style="{ 'border-top': `3px solid ${card.color}` }"
  >
    <div class="card__header">
      <span class="title">{{ card.title }}</span>
      <span
        ><b-icon :style="{ color: card.color }" :icon="card.icon"></b-icon
      ></span>
    </div>
    <div class="card__value">
      <span>{{ card.value }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["card"],
};
</script>

<style lang="scss">
.status__card {
  width: 258px;
  // box-shadow: 0px -2px 0px #ffaa2c, 0px 2px 11px rgba(0, 0, 0, 0.06);
  border-radius: 4px;
  padding: 20px;
  // width: 100%;
  box-shadow: 0px 2px 11px 0px rgba(0, 0, 0, 0.06);
  .card__header {
    display: flex;
    justify-content: space-between;
    gap: 16px;
  }
  .card__value {
    font-size: 24px;
    font-weight: 600;
  }
}
</style>
