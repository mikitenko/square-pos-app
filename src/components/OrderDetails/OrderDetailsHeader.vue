<template>
  <div class="order-details-header">
    <div class="close-icon-box">
      <div @click.prevent="closeApp" class="close"></div>
    </div>
    <div class="order-details-header-title roboto-bold">Order details</div>
  </div>
</template>

<script>
export default {
  name: "OrderDetailsHeader",
  props: {
    order: {
      required: true,
      type: Object
    }
  },
  methods: {
    closeApp() {
      window.parent.postMessage(`scandi-close-app`, "*");
      window.parent.postMessage(
        `scandi-update-chatpage-messages:${JSON.stringify(
          this.order.order_info
        )}`,
        "*"
      );
    }
  }
};
</script>

<style lang="scss" scoped>
.order-details-header {
  height: 60px;
  display: flex;
  width: 100%;
  background: #ffffff;

  &-title {
    display: flex;
    align-items: center;
    justify-content: center;
    width: calc(100% + 36px);
    font-size: 16px;
  }

  .close-icon-box {
    cursor: pointer;
    .close {
      position: absolute;
      left: 12px;
      top: 18px;
      width: 24px;
      height: 24px;
      opacity: 0.8;
    }
    .close:hover {
      opacity: 1;
    }
    .close:before,
    .close:after {
      position: absolute;
      left: 10px;
      content: " ";
      height: 24px;
      width: 3px;
      background-color: #000000;
    }
    .close:before {
      transform: rotate(45deg);
    }
    .close:after {
      transform: rotate(-45deg);
    }
  }
}
</style>
