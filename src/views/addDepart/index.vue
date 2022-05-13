<template>
  <div>
    <h1>添加科室</h1>
    <el-form ref="form" :model="form" label-width="80px">
      <el-form-item label="医院名称">
        <el-input v-model="form.hosName" />
      </el-form-item>
      <el-form-item label="科室名称">
        <el-input v-model="form.departName" />
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
        hosName: '',
        departName: ''
      }
    }
  },
  methods: {

    mysubmit() {
      const fd = new FormData()
      fd.append('hosName', this.form.hosName)
      fd.append('departName', this.form.departName)
      axios({
        url: 'http://182.61.53.38:8080/hospital/addDepart',
        method: 'post',
        data: fd,
        headers: {
          'Content-Type': 'multipart/form-data'

        }
      }).then(res => {
        console.log(res)
      })
      alert('提交科室成功')
    }
  }
}
</script>
