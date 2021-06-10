<template>
  <div class="gender-container">
    <div class="box-gender" :class="{error : isError}">
      <div class="box-gender-input">
        <input
          type="text"
          placeholder=""
          v-model="genderName"
          @keyup="FindGender()"
          @keyup.down="SelectGender"
          @click="ActiveContent"
        />
      </div>
      <div class="box-gender-icon" @click="ActiveContent"></div>
    </div>
    <div class="gender-content" v-bind:class="{isActiveContent : isActiveContent}">
      <div
        class="gender"
        v-for="(gender, index) in genders"
        :key="index"
        @click="ChooseGender(gender.value, gender.name)"
        v-bind:class="[BindClass(gender), { isActived: isActive }]"
        :select-om-keycode="12"
      >
        <div class="icon-selected"></div>
        <div class="gender-content-text">{{ gender.name }}</div>
      </div>
    </div>
  </div>
</template>
<script>
import $ from 'jquery'
export default {
  name: 'DropDownGender',
  data () {
    return {
      genders: [
        { value: 0, name: 'Nữ' },
        { value: 1, name: 'Nam' },
        { value: 2, name: 'Khác' }
      ],
      genderSelected: {
        value: null,
        name: null
      },
      isActive: false,
      genderName: '',
      isActiveContent: false,
      isError: false, // lỗi
      isChoose: false // gender được chọn
    }
  },
  methods: {
    FindGender () {
      // Giới tính được chọn sẽ có background xanh
      var keyword = this.genderName.charAt(0).toUpperCase() + this.genderName.slice(1)
      var count = 0
      if (this.genderName === '' || typeof this.genderName !== 'undefined') {
        this.genders.forEach(element => {
          $('.gender' + element.value).removeClass('valueFound', 'valueNotFound')
        })
      }
      this.genders.forEach((element) => {
        var index = element.value
        this.isActiveContent = true
        if (element.name.indexOf(keyword) !== -1) {
          $('.gender' + index).removeClass('valueNotFound')
          $('.gender' + index).addClass('valueFound')
        } else {
          $('.gender' + index).removeClass('valueFound')
          $('.gender' + index).addClass('valueNotFound')
          count++
        }
      })
      if (count === this.genders.length) {
        this.isError = true
        this.isActiveContent = false
      } else {
        this.isError = false
      }
    },
    SelectGender () {

    },
    ChooseGender (val, name) {
      this.genderSelected.value = val
      this.genderSelected.name = name
      this.genderName = name
      this.isActiveContent = false
      this.isError = false
      this.genders.forEach(element => {
        var index = element.value
        if (element.name.indexOf(this.genderSelected.name) !== -1) {
          $('.gender' + index).addClass('isChoosed')
          $('.icon-selected' + index).addClass('isChoosed')
        } else {
          $('.gender' + index).removeClass('isChoosed')
        }
      })
    },
    BindClass (val) {
      return 'gender' + val.value
    },
    ActiveContent () {
      this.isActiveContent = !this.isActiveContent
      this.genders.forEach(element => {
        var index = element.value
        if (element.name.indexOf(this.genderSelected.name) !== -1) {
          $('.gender' + index).addClass('isChoosed', 'gender-content-icon')
        }
      })
    }
  }
}
</script>
<style scoped>
@import url("./DropDown.css");
</style>
