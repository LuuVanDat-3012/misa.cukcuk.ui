<template>
  <div class="body-left" :class="{ zoomOut: isZoom }">
    <div class="sidebar" :class="{ zoomOutSiderBar: isZoom }">
      <div class="box-logo">
        <div class="toggle" @click="ZoomOut"></div>
        <div class="logo" v-if="isActived"></div>
      </div>
    </div>

    <div class="menu">
      <div class="menu-item">
        <div class="icon overview"></div>
        <transition
          name="custom-classes-transition"
          enter-active-class="animated tada"
          leave-active-class="animated bounceOutRight"
        >
          <div class="menu-item-text" v-if="isActived">Tổng quan</div>
        </transition>
      </div>
      <div class="menu-item">
        <div class="icon report"></div>
        <transition
          name="custom-classes-transition"
          enter-active-class="animated tada"
          leave-active-class="animated bounceOutRight"
        >
          <div class="menu-item-text" v-if="isActived">Báo cáo</div>
        </transition>
      </div>
      <div class="menu-item">
        <div class="icon buy"></div>
        <transition
          name="custom-classes-transition"
          enter-active-class="animated tada"
          leave-active-class="animated bounceOutRight"
        >
          <div class="menu-item-text" v-if="isActived">Mua hàng</div>
        </transition>
      </div>
      <div class="menu-item">
        <div class="icon list-employee"></div>
        <transition
          name="custom-classes-transition"
          enter-active-class="animated tada"
          leave-active-class="animated bounceOutRight"
        >
          <div class="menu-item-text" v-if="isActived">Danh mục nhân viên</div>
        </transition>
      </div>
      <div class="menu-item">
        <div class="icon setting"></div>
        <transition
          name="custom-classes-transition"
          enter-active-class="animated tada"
          leave-active-class="animated bounceOutRight"
        >
          <div class="menu-item-text" v-if="isActived">Thiết lập hệ thống</div>
        </transition>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'LeftSideBar',
  methods: {
    ZoomOut () {
      this.isActived = !this.isActived
      this.isZoom = !this.isZoom
      this.$emit('Zoom', this.isZoom)
    }
  },
  data () {
    return {
      isActived: true,
      isZoom: false
    }
  }
}
</script>
<style>
.body-left {
  background-color: #ffffff;
  width: 226px;
  height: 100vh;
  display: flex;
  flex-direction: column;
  border-right: 1px solid #d2d2d2;
}
.menu-item-text {
  min-width: 150px;
}

.body-left .sidebar {
  height: 60px;
  display: flex;
  width: 226px;
}
.body-left .sidebar .box-logo {
  width: 202px;
  height: 24px;
  position: absolute;
  top: 16px;
  left: 16px;
  display: flex;
}

.body-left .sidebar .box-logo .toggle {
  width: 24px;
  height: 24px;
  background-image: url("../../assets/image/toggle.png");
  background-repeat: no-repeat;
  background-size: contain;
  cursor: pointer;
}

.body-left .sidebar .box-logo .logo {
  flex: 1;
  height: 24px;
  background-image: url("../../assets/image/cukcuk-logo.png");
  background-size: contain;
  background-repeat: no-repeat;
  cursor: pointer;
  margin-left: 16px;
}

.body-left .menu {
  position: relative;
  flex: 1;
}

.body-left .menu .menu-item {
  display: flex;
  align-items: center;
  cursor: pointer;
  height: 44px;
  padding-left: 16px;
}

.body-left .menu .menu-item .menu-item-text {
  margin-left: 16px;
}
.body-left .menu .menu-item:hover {
  background-color: #e9ebee;
}

.body-left .menu .menu-item .icon {
  width: 20px;
  height: 20px;
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
}
.icon {
  width: 50px;
  height: 100%;
  box-sizing: border-box;
}
.body-left .menu .menu-item .icon.overview {
  background-image: url("../../assets/icon/dashboard.png");
}

.body-left .menu .menu-item .icon.report {
  background-image: url("../../assets/icon/report.png");
}

.body-left .menu .menu-item .icon.buy {
  background-image: url("../../assets/icon/dashboard.png");
}
.body-left .menu .menu-item .icon.list-employee {
  background-image: url("../../assets/icon/dic-employee.png");
}
.body-left .menu .menu-item .icon.setting {
  background-image: url("../../assets/icon/setting.png");
}

.body-left .menu .menu-item .item-name {
  width: 150px;
}

.isBlack {
  background-color: #ccc;
  z-index: 9;
  opacity: 0.6;
}

.zoomOut {
  width: 50px;
}
.zoomOutSiderBar {
  width: 41px !important;
}
</style>
