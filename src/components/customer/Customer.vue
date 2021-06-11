<template>
  <div>
    <Header @ShowDialog="ShowDialog" />
    <FilterCustomer
      @GetFilter="GetFilter"
      @DeleteCustomers="DeleteCustomers"
      @ReloadData='ReloadData'
      ref=""
    />
    <Grid @ShowCustomerDetail="ShowCustomerDetail" ref="grid" @GetViewData="GetViewData"/>
    <CustomerDetail
      v-show="isShowed"
      @CloseDialog="CloseDialog"
      ref="CustomerDetail"
      :statusMethod='this.statusMethod'
       @ReloadData="ReloadData"
    />
    <PopupDetele
      v-show="isShowPopup"
      @ClosePopup="isShowPopup = false"
      :listIdDeleted="this.listIdDeleted"
      @ReloadData="ReloadData"
    />
    <MISANavigate ref="MISANavigate" @GetCustomerPaging='GetCustomerPaging' :totalPage="this.page.totalPage" :pageIndex="this.page.pageIndex" />
  </div>
</template>
<script>
import MISANavigate from './navigate/index.vue'
import Header from './header/index.vue'
import FilterCustomer from './filter/index.vue'
import Grid from './grid/index.vue'
import CustomerDetail from './customer_detail/index.vue'
import PopupDetele from './popup/PopupDetele.vue'
export default {
  name: 'Customer',
  components: {
    Header,
    FilterCustomer,
    Grid,
    CustomerDetail,
    PopupDetele,
    MISANavigate
  },
  setup () {},
  data () {
    return {
      // Hiện thị customerdetai
      isShowed: false,
      // Biến hiện thị popup delete
      isShowPopup: false,
      // Khởi tạo 1 khách hàng rỗng
      // Danh sách id cần xoá
      listIdDeleted: [],
      statusMethod: '',
      viewData: '',
      page: {
        pageIndex: 1,
        pageSize: 30,
        totalPage: 1,
        filter: ''
      },
      infoCustomer: {
        id: '2924c34d-68f1-1d0a-c9c7-6c0aeb6ec302',
        customerCode: '',
        fullname: '',
        gender: 1,
        birthday: '2000-12-30T00:00:00',
        phone: '',
        email: '',
        memberCardCode: '',
        taxCode: '',
        address: '',
        company: '',
        customerGroupName: 'Thường',
        customerGroupId: '2924c34d-68f1-1d0a-c9c7-6c0aeb6ec302',
        status: '1',
        editMode: 0
      }
    }
  },
  methods: {
    // Hiển thị customer detail - thêm mới
    ShowDialog () {
      this.isShowed = true
      this.statusMethod = 'POST'
      this.$refs.CustomerDetail.FocusInput()
    },
    // Hiện thị customer detail - sửa
    ShowCustomerDetail (customerId) {
      this.statusMethod = 'PUT'
      this.isShowed = true
      this.$refs.CustomerDetail.ShowCustomerDetail(customerId)
      this.$refs.CustomerDetail.FocusInput()
    },
    // Đóng customer detail
    CloseDialog () {
      this.isShowed = false
    },
    // Gọi hàm hiển thị customer và truyền tên cần tìm
    GetFilter (filter) {
      this.page.filter = filter
      this.$refs.grid.ShowCustomers(this.page.pageIndex, this.page.pageSize, this.page.filter)
      // Truyền số trangcho navigate
    },
    DeleteCustomers () {
      this.listIdDeleted = this.$refs.grid.listIdDeleted
      if (this.listIdDeleted.length === 0) {
        this.$vToastify.warning('Vui lòng chọn các khách hàng muốn xoá !!!')
      } else {
        this.isShowPopup = true
      }
    },
    // Tải lại dữ liệu
    ReloadData () {
      this.listIdDeleted = []
      this.$refs.grid.listIdDeleted = []
      this.$refs.grid.ReloadData()
    },
    // Hàm lấy ra tổng số trang
    GetViewData (val) {
      this.page.totalPage = val.totalPage
      this.page.pageIndex = val.pageNum
    },
    // Hàm nhận ví trị trangm uốn đến
    GetCustomerPaging (pageIndex) {
      this.$refs.grid.ShowCustomers(pageIndex, this.page.pageSize, this.page.filter)
    }
  }
}
</script>
<style></style>
