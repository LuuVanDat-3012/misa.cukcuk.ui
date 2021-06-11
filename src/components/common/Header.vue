<template>
  <div class="header" :class="{ enlarge: isEnlarge }">
    <div class="res">
    </div>
    <div class="user">
      <div class="image-user"></div>
      <div class="username">Lưu Văn Đạt</div>
      <div class="more-info"></div>
    </div>
  </div>
</template>
<script>

export default {
  components: { },
  name: 'Header',
  data () {
    return {
      isEnlarge: false
    }
  }

}
</script>
<style>
.header {
  display: flex;
  position: absolute;
  width: calc(100% - 227px);
  right: 0;
  height: 60px;
  top: 0;
  display: flex;
  align-items: center;
}
.res select {
  border: 0;
  width: 200px;
  font-family: MISA-Regular;
  font-size: 15px;
  padding-left: 24px;
  font-weight: bolder;
}
.res select:focus {
  outline: 0;
}
.user {
  display: flex;
  position: absolute;
  right: 24px;
}
.image-user {
  width: 30px;
  height: 30px;
  background-image: url("../../assets/icon/avatar-default.png");
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
  border-radius: 50%;
}
.username {
  padding: 0px 16px 0px 16px;
  line-height: 30px;
}
.more-info {
  width: 30px;
  height: 30px;
  background-image: url("../../assets/icon/option.png");
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;
}
.enlarge {
  width: calc(100% - 41px);
  left: 41px;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
