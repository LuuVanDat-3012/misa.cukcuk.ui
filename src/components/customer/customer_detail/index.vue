<template>
  <div class="container-dialog">
    <div class="dialog-model"></div>
    <div class="dialog">
      <div class="dialog-title">
        <div class="dialog-title-text">THÔNG TIN KHÁCH HÀNG</div>
        <div class="btn-close-dialog" @click="CloseDialog"></div>
      </div>
      <div class="dialog-content">
        <div class="content-up">
          <div class="input-image">
            <div class="image-icon">
              <div></div>
            </div>
            <div class="image-text">
              <div>Vui lòng chọn ảnh có định dạng <b>.jpg, .png, .gif</b></div>
            </div>
          </div>
          <div class="input-info-up">
            <div class="box-input-up">
              <div class="input-code input-common">
                <div class="input-title">
                  Mã khách hàng <b style="color: red">(*)</b>
                </div>
                <div class="input-box">
                  <input
                    type="text"
                    ref="autofocus"
                    class="imposition"
                    v-model="infoCustomer.customerCode"
                    :class="{ warning: isWarningCode }"
                    @keyup="isWarningCode = false"
                    placeholder=" Mã khách hàng "
                  />
                </div>
              </div>
              <div class="input-code input-common">
                <div class="input-title">
                  Họ và tên <b style="color: red">(*)</b>
                </div>
                <div class="input-box">
                  <input
                    type="text"
                    name="CFullname"
                    class="imposition"
                    v-model="infoCustomer.fullname"
                    placeholder="Họ và tên"
                    :class="{ warning: isWarningName }"
                    @keyup="isWarningName = false"
                  />
                </div>
              </div>
            </div>

            <div class="box-input-up">
              <div class="input-code-card input-common">
                <div class="input-title">Mã thẻ thành viên</div>
                <div class="input-box">
                  <input
                    type="text"
                    name="memberCardCode"
                    v-model="infoCustomer.memberCardCode"
                    placeholder="Mã thẻ thành viên"
                  />
                </div>
              </div>
              <div class="input-code-card input-common">
                <div class="input-title">Nhóm khách hàng</div>
                <div class="input-box">
                  <Combobox
                    @GetCustomerGroup="GetCustomerGroup"
                    ref="combobox"
                  />
                </div>
              </div>
            </div>
            <div class="box-input-up">
              <div class="input-birthday input-common">
                <div class="input-title">Ngày sinh</div>
                <div class="input-box">
                  <!-- <input
                    type="date"
                    name="CBirthday"
                    v-model="infoCustomer.birthday"
                    placeholder="dd/MM/yyyy"
                  /> -->
                  <DatePicker
                    class="datepicker"
                    v-model="infoCustomer.birthday"
                    format="dd/MM/yyyy"
                    :class="{warning : isWarningDate}"
                  />
                </div>
              </div>
              <div class="input-birthday input-common">
                <div class="input-title">Giới tính</div>
                <div class="input-box radioGender">
                  <div class="male">
                    <input
                      type="radio"
                      name="customerGender"
                      value="0"
                      id="nam"
                      v-model="infoCustomer.gender"
                    />
                    <label for="nam">Nam</label>
                  </div>
                  <div class="female">
                    <input
                      type="radio"
                      name="customerGender"
                      value="1"
                      id="nu"
                      v-model="infoCustomer.gender"
                    />
                    <label for="nu">Nữ</label>
                  </div>
                  <div class="other">
                    <input
                      type="radio"
                      name="customerGender"
                      value="2"
                      id="khac"
                      v-model="infoCustomer.gender"
                    />
                    <label for="khac">Khác</label>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- NỬA DƯỚI -->
        <div class="input-center">
          <div class="input-center-row">
            <div class="input-center-left">
              <div class="input-title">Email</div>
              <div class="box-center-left">
                <input
                  type="email"
                  name="customerEmail"
                  placeholder="example@gmail.com"
                  v-model="infoCustomer.email"
                  @keyup="/^[\+]?[(]?[0-9]{3}[)]?[-\s\.]?[0-9]{3}[-\s\.]?[0-9]{4,6}$/im"
                />
              </div>
            </div>
            <div class="input-center-right">
              <div class="input-code-card input-common">
                <div class="input-title">
                  Số điện thoại <b style="color: red">(*)</b>
                </div>

                <div class="input-box">
                  <input
                    type="text"
                    class="imposition"
                    v-model="infoCustomer.phone"
                    placeholder="Sô điện thoại"
                    :class="{ warning: isWarningPhone }"
                    @keyup="isWarningPhone = false"
                  />
                </div>
              </div>
            </div>
          </div>

          <div class="input-center-row">
            <div class="input-center-left">
              <div class="input-title">Tên công ty</div>
              <div class="box-center-left">
                <input
                  type="text"
                  name="CCompany"
                  v-model="infoCustomer.company"
                  placeholder="Tên công ty"
                />
              </div>
            </div>
            <div class="input-center-right">
              <div class="input-code-card input-common">
                <div class="input-title">Mã số thuế</div>
                <div class="input-box">
                  <input
                    type="text"
                    name="CTaxCode"
                    placeholder="Mã số thuế"
                    v-model="infoCustomer.taxCode"
                  />
                </div>
              </div>
            </div>
          </div>

          <div class="input-center-row">
            <div class="input-center-address">
              <div class="input-title">Địa chỉ</div>
              <div class="box-center-address">
                <input
                  type="text"
                  name="CAddress"
                  v-model="infoCustomer.address"
                />
              </div>
            </div>
          </div>
        </div>
        <!-- FOOTER -->
        <div class="dialog-footer">
          <div class="btn-cancel" @keyup.enter="CloseDialog">
            <button @click="CloseDialog">HUỶ</button>
          </div>
          <div class="btn-save" @keyup.enter="SaveCustomer" >
            <button @click="SaveCustomer">{{ StatusMethod }}</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import DatePicker from 'vuejs-datepicker'
import Combobox from '../combobox/index'
import moment from 'moment'
export default {
  name: 'CustomerDetai',
  components: {
    DatePicker,
    Combobox
  },
  data () {
    return {
      infoCustomer: {
        customerId: '2924c34d-68f1-1d0a-c9c7-6c0aeb6ec302',
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
      },
      isDisabled: false,
      isWarningName: false,
      isWarningCode: false,
      isWarningPhone: false,
      tmp: {
        customerId: '2924c34d-68f1-1d0a-c9c7-6c0aeb6ec302',
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
      },
      isWarningDate: false
    }
  },
  props: {
    statusMethod: {
      typeof: String
    }
  },

  methods: {
    CustomFormatter (val) {
      return moment(val, 'YYYY-MM-DD')
    },
    ShowCustomerDetail (val) {
      if (val !== '') {
        this.axios.get('Customers/' + val).then((response) => {
          if (response.data.data != null) {
            this.infoCustomer = response.data.data[0]
            this.$refs.combobox.customerGroupSelected.customerGroupId = response.data.data[0].customerGroupId
            this.$refs.combobox.customerGroupSelected.customerGroupName = response.data.data[0].customerGroupName
          }
        })
      }
    },
    FocusInput () {
      setTimeout(() => {
        this.$refs.autofocus.focus()
      }, 10)
    },

    ValidateData (val) {
      if (typeof val === 'undefined' || val === null || val === '') {
        return false
      }
      return true
    },
    ValidateCustomer () {
      if (this.ValidateData(this.infoCustomer.customerCode) === false) {
        this.isWarningCode = true
        return false
      }
      if (this.ValidateData(this.infoCustomer.fullname) === false) {
        this.isWarningName = true
        return false
      }
      if (this.ValidateData(this.infoCustomer.phone) === false) {
        this.isWarningPhone = true
        return false
      }
      // var minDate = moment(2001, 1, 1)
      // var maxDate = moment(2020, 1, 1)
      // if (this.infoCustomer.birthday > maxDate || this.infoCustomer.birthday < minDate) {
      //   this.isWarningDate = true
      //   return false
      // }
      if (this.ValidateData(this.infoCustomer.phone) === false) {
        this.isWarningPhone = true
        return false
      }
      return true
    },
    SaveCustomer () {
      // this.infoCustomer.birthday = this.CustomFormatter(this.infoCustomer.birthday)
      // console.log(this.infoCustomer.birthday)
      if (this.ValidateCustomer()) {
        var listCustomer = []
        // nếu method là post sẽ thêm mới khách hàng
        if (this.statusMethod === 'POST') {
          this.infoCustomer.editMode = 1
        }
        if (this.statusMethod === 'PUT') {
          this.infoCustomer.editMode = 2
        }
        listCustomer.push(this.infoCustomer)
        this.axios
          .post('Customers', listCustomer)
          .then((response) => {
            if (response.data.success === true) {
              this.$vToastify.success(response.data.message)
              this.CloseDialog()
              this.$emit('ReloadData')
            } else {
              this.$vToastify.error(response.data.message)
              const listFieldNotValid = response.data.fieldNotValids
              listFieldNotValid.forEach(element => {
                this.$vToastify.error(element.msg)
              })
            }
          })
          .catch((exp) => {
            this.$vToastify.error('Đã xảy ra lỗi !!!')
          })
      }
    },
    GetCustomerGroup (id, name) {
      this.infoCustomer.customerGroupId = id
      this.infoCustomer.customerGroupName = name
    },
    CloseDialog () {
      this.isWarningName = false
      this.isWarningCode = false
      this.isWarningPhone = false
      this.infoCustomer = this.tmp
      this.$refs.combobox.isClick = false
      this.$emit('CloseDialog')
    },
    ValidateEmail (email) {
      var regex = '/^[\\+]?[(]?[0-9]{3}[)]?[-\\s\\.]?[0-9]{3}[-\\s\\.]?[0-9]{4,6}$/im'
      var result = email.match(regex)
      console.log(email)
      return result
    }
  },
  mounted () {
    this.FocusInput()
  },
  computed: {
    StatusMethod () {
      if (this.statusMethod === 'POST') {
        return 'LƯU'
      }
      return 'SỬA'
    }
  }
}
</script>
<style>
@import url("./customer_detail.css");
</style>
