<template>
  <div class="dropdown">
    <div class="dropbtn">
      <div class="dropbtn-text">{{ customerGroupSelected.customerGroupName }}</div>
      <div class="dropbtn-icon" @click="isClick = !isClick"></div>
    </div>
    <div class="drop-content" v-show="isClick">
      <div
        class="item"
        v-for="(item, index) in customerGroup"
        :key="index"
        @click="GetCustomerGroup(item.customerGroupId, item.customerGroupName)"
      >
        <div class="content-icon-default"></div>
        <div class="cbb-content-text">{{ item.customerGroupName }}</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  data () {
    return {
      customerGroup: null,
      isHover: false,
      isClick: false,
      customerGroupSelected: {
        customerGroupId: '',
        customerGroupName: ''
      }
    }
  },
  methods: {
    GetCustomerGroup (id, name) {
      this.customerGroupSelected.customerGroupName = name
      this.customerGroupSelected.customerGroupId = id
      this.$emit('GetCustomerGroup', id, name)
      this.isClick = false
    }
  },
  mounted () {
    this.axios('CustomerGroups?pageIndex=1&pageSize=100').then(response => {
      this.customerGroup = response.data.data
      this.customerGroupSelected.customerGroupId = response.data.data[0].customerGroupId
      this.customerGroupSelected.customerGroupName = response.data.data[0].customerGroupName
    })
  },
  props: {

  }
}
</script>
<style>
@import url("./combobox.css");
</style>
