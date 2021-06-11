<template>
  <div class="MISAnavigate">
    <div class="total-employee">Hiển thị nhân viên trên một trang:</div>
    <div class="list-page-number">
      <div class="page">
        <div class="btn-firstpage navigate-page"></div>
        <div class="btn-prev-page navigate-page"></div>
        <div  v-for="index in 4" :key="index"  @click="GetCustomerPaging(index)">
          <div class="page-number">{{index}}</div>
        </div>
        <div class="btn-next-page navigate-page"></div>
        <div class="btn-lastpage navigate-page"></div>
      </div>
    </div>
    <div class="employees-in-page">Tổng: {{totalPage}}</div>
  </div>
</template>
<script>
export default {
  name: 'MISANavigate',
  data () {
    return {
      currentPage: 1
    }
  },
  methods: {

    Selected (val) {
      if (val - 1 === this.page) { return true }
    },
    GetCustomerPaging (pageIndex) {
      this.$emit('GetCustomerPaging', pageIndex)
    }
  },
  props: {
    totalPage: {
      typeof: Number,
      default: 1
    },
    pageIndex: {
      typeof: Number,
      default: 1
    }
  }

}
</script>
<style>
@import url("./navigate.css");
</style>
