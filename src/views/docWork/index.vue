<template>
  <div>
    <h1>医生排班</h1>
    <el-form ref="form" :model="form" label-width="80px">
      <el-form-item label="医生工号">
        <el-input v-model="form.workId" />
      </el-form-item>
      <el-form-item label="工作日期">
        <div class="block">
          <span class="demonstration" />
          <el-date-picker
            v-model="form.value1"
            value-format="yyyy-MM-dd"
            type="daterange"
            range-separator="至"
            start-placeholder="开始日期"
            end-placeholder="结束日期"
          />
        </div>
      </el-form-item>
      <el-form-item label="挂号价格">
        <el-input v-model="form.price" />
      </el-form-item>
      <el-form-item label="时段1余号">
        <el-input v-model="form.surplusOne" />
      </el-form-item>
      <el-form-item label="时段2余号">
        <el-input v-model="form.surplusTwo" />
      </el-form-item>
      <el-form-item label="时段3余号">
        <el-input v-model="form.surplusThree" />
      </el-form-item>
      <el-form-item label="时段4余号">
        <el-input v-model="form.surplusFour" />
      </el-form-item>
      <el-form-item label="时段5余号">
        <el-input v-model="form.surplusFifve" />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="mysubmit">提交</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data() {
    return {
      form: {
        workId: '',
        value1: '',
        price: '',
        surplusOne: '',
        surplusTwo: '',
        surplusThree: '',
        surplusFour: '',
        surplusFifve: ''

      },
      workinfo: {
        docId: '',
        beginWorkDate: '',
        endWorkDate: '',
        decimal: '',
        surplusNumEight: '',
        surplusNumNine: '',
        surplusNumTen: '',
        surplusNumFourteen: '',
        surplusNumFifteen: ''
      }
    }
  },
  methods: {

    mysubmit() {
      this.workinfo.docId = this.form.workId
      this.workinfo.beginWorkDate = this.form.value1[0]
      this.workinfo.endWorkDate = this.form.value1[1]
      this.workinfo.decimal = this.form.price
      this.workinfo.surplusNumEight = this.form.surplusOne
      this.workinfo.surplusNumNine = this.form.surplusTwo
      this.workinfo.surplusNumTen = this.form.surplusThree
      this.workinfo.surplusNumFourteen = this.form.surplusFour
      this.workinfo.surplusNumFifteen = this.form.surplusFifve

      console.log(this.workinfo)
      axios({
        url: 'http://182.61.53.38:8080/admin/updateDocWorkInfo',
        method: 'post',
        data: this.workinfo

      }).then(res => {
        console.log(res)
      })
      alert('医生排班成功')
    }
  }
}
</script>
