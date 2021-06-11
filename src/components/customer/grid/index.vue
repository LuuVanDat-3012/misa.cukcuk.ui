<template>
  <div class="grid">
    <div class="grid-view">
      <div class="grid-model-control">
        <div class="ms-grid-viewer table-scrol">
          <table class="ms-table-viewer">
            <thead class="ms-thead-viewer">
              <tr class="ms-tr-viewer">
                <th class="ms-th-viewer ms-muli-checkall">
                  <input type="checkbox" class="ms-input-checkall" />
                </th>
                <div class="dis-contents ms-tbody-viewer">
                  <!-- Mã khách hàng -->
                  <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                        Mã khách hàng
                      </span>
                    </div>
                  </th>
                  <!-- Tên khách hang -->
                  <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                        Tên khách hàng
                      </span>
                    </div>
                  </th>
                  <!-- Giới tính -->
                  <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                        Giới tính
                      </span>
                    </div>
                  </th>
                  <!-- Ngày sinh -->
                  <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                        Ngày sinh
                      </span>
                    </div>
                  </th>
                  <!-- Số điện thoại -->
                  <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                        Số điện thoại
                      </span>
                    </div>
                  </th>
                  <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                        Email
                      </span>
                    </div>
                  </th>
                  <!-- Nhóm khách hàng -->
                  <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                        Nhóm khách hàng
                      </span>
                    </div>
                  </th>
                  <!-- Mã thẻ thành viên -->
                   <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                        Mã thẻ thành viên
                      </span>
                    </div>
                  </th>
                  <!-- Mã số thuế -->
                   <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                       Mã số thuế
                      </span>
                    </div>
                  </th>
                  <!-- Địa chỉ công ty -->
                   <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                      Địa chỉ
                      </span>
                    </div>
                  </th>
                   <th class="ms-th-viewer dynamic-col header-col">
                    <div class="col-draggable">
                      <span class="ms-head-title justify-left flex">
                      Công ty
                      </span>
                    </div>
                  </th>
                </div>
              </tr>
            </thead>

            <!-- Nội dung -->
            <tbody>
              <tr class="ms-tr-viewer revenue-status-undifined row-selected" v-for="(customer, index) in listCustomer" :key="index" @dblclick="ShowCustomerDetail(customer.customerId)">
                  <td class="ms-td-viewer ms-td-multi">
                    <label for="" class="ms-component center con-ms-checkbox">
                      <input type="checkbox" class="ms-checkbox--input" :value="customer" :id="customer" v-model="listIdDeleted">
                    </label>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.customerCode}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.fullname}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.gender | formatGender}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.birthday | formatDate}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.phone}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.email}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.customerGroupName}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.memberCardCode}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.taxCode}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.address}}
                        </span>
                      </span>
                    </span>
                  </td>
                  <td class="ms-td-viewer text-left">
                    <span>
                      <span>
                        <span>
                              {{customer.company}}
                        </span>
                      </span>
                    </span>
                  </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
    <div class="loading" v-if="isLoading">
      <PulseLoader class="loading-icon"></PulseLoader>
    </div>
  </div>
</template>
<script>
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'
export default {
  name: 'Grid',
  components: {
    PulseLoader
  },
  data () {
    return {
      listCustomer: 1,
      isShow: false,
      isLoading: true,
      listIdDeleted: []
    }
  },
  methods: {
    ShowCustomerDetail (customerId) {
      this.$emit('ShowCustomerDetail', customerId)
    },
    // Danh sách khách hàng theo tên
    ShowCustomers (pageIndex, pageSize, filter) {
      this.isLoading = true
      this.axios
        .get('Customers?pageIndex=' + pageIndex + '&pageSize=' + pageSize + '&filter=' + filter)
        .then((response) => {
          this.listCustomer = response.data.data
          this.$emit('GetViewData', response.data)
          this.isLoading = false
        })
    },
    ReloadData () {
      console.log('Da dc goi')
      this.isLoading = true
      this.axios.get('Customers?pageIndex=1&pageSize=30').then((response) => {
        this.listCustomer = response.data.data
        this.isLoading = false
      })
    }
  },
  computed: {
    ConvertToString () {
      return this.listIdDeleted.join("','")
    }
  },
  mounted () {
    this.axios.get('Customers?pageIndex=1&pageSize=30').then((response) => {
      this.listCustomer = response.data.data
      this.isLoading = false
      // Lấy tổng số trang
      this.$emit('GetViewData', response.data)
    })
  }
}
</script>

<style>
@import url("./grid.css");
</style>
