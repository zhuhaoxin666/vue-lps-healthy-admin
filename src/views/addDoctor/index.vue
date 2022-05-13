<template>
  <div>
    <h1>新增医生</h1>
    <el-form ref="form" :model="form" label-width="80px">
      <el-form-item label="医院名称">
        <el-input v-model="form.hosName" />
      </el-form-item>
      <el-form-item label="科室名称">
        <el-input v-model="form.departName" />
      </el-form-item>
      <el-form-item label="用户名">
        <el-input v-model="form.nickName" />
      </el-form-item>
      <el-form-item label="医生姓名">
        <el-input v-model="form.docName" />
      </el-form-item>
      <el-form-item label="密码">
        <el-input v-model="form.password" type="password" />
      </el-form-item>
      <el-form-item label="医生级别">
        <el-input v-model="form.docLevel" />
      </el-form-item>
      <el-form-item label="角色" hidden>
        <el-input v-model="form.role" />
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
        departName: '',
        nickName: '',
        docName: '',
        password: '',
        role: 'doctor',
        docLevel: ''
      }
    }
  },
  methods: {

    mysubmit() {
      axios({
        url: 'http://182.61.53.38:8080/hospital/addDoctor',
        method: 'post',
        data: this.form

      }).then(res => {
        console.log(res)
      })
      alert('添加医生成功')
    }
  }
}
</script>
