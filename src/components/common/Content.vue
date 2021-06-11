<template>
  <transition name="fade">
    <div class="content" :class="{ enlarge: isEnlarge }">
      <!-- <div class="navigation"></div> -->
      <Customer />
    </div>
    \</transition
  >
</template>
<script>
import Customer from '../customer/Customer'
// eslint-disable-next-line import/extensions

export default {
  components: {
    Customer
  },
  data () {
    return {
      isEnlarge: false
    }
  }
}
</script>
<style>
.content {
  width: calc(100% - 227px);
  height: calc(100vh - 61px);
  position: absolute;
  top: 61px;
  left: 227px;
  display: flex;
  flex-direction: column;
  padding: 0px 24px 0px 24px;
  box-sizing: border-box;
  border-top: 1px solid #d2d2d2;
}
.enlarge {
  width: calc(100% - 50px);
  left: 50px;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
