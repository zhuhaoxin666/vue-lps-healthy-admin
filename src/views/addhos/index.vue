<template>
  <div>
    <h1>添加医院</h1>
    <el-form ref="form" :model="form" label-width="80px">
      <el-form-item label="医院名称">
        <el-input v-model="form.hosName" />
      </el-form-item>
      <el-form-item label="医院等级">
        <el-input v-model="form.hosLevel" />
      </el-form-item>
      <el-form-item label="医院性质">
        <el-input v-model="form.hosNature" />
      </el-form-item>
      <el-form-item label="医院类别">
        <el-input v-model="form.hosCategory" />
      </el-form-item>
      <el-form-item label="医院地址">
        <el-input v-model="form.hosAddress" />
      </el-form-item>
      <el-form-item label="医院介绍">
        <el-input v-model="form.hosIntroduce" type="textarea" />
      </el-form-item>
      <el-form-item label="医院电话">
        <el-input v-model="form.hosTelephone" />
      </el-form-item>
      <el-form-item label="医院图片">
        <input ref="input" type="file" @change="handleFiles">
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
        imgFile: null,
        hosName: '',
        hosLevel: '',
        hosNature: '',
        hosCategory: '',
        hosAddress: '',
        hosIntroduce: '',
        hosTelephone: ''
      }
    }
  },
  methods: {
    handleFiles(event) {
      this.form.imgFile = event.target.files[0]
      console.log(this.form.imgFile)
    },
    mysubmit() {
      const fd = new FormData()
      fd.append('imgFile', this.form.imgFile) // 传文件
      fd.append('hosName', this.form.hosName)
      fd.append('hosLevel', this.form.hosLevel)
      fd.append('hosNature', this.form.hosNature)
      fd.append('hosCategory', this.form.hosCategory)
      fd.append('hosAddress', this.form.hosAddress)
      fd.append('hosIntroduce', this.form.hosIntroduce)
      fd.append('hosTelephone', this.form.hosTelephone)
      axios({
        url: 'http://182.61.53.38:8080/hospital/addHospital2',
        method: 'post',
        data: fd,
        headers: {
          'Content-Type': 'multipart/form-data'

        }
      }).then(res => {
        console.log(res)
      })
      alert('提交成功')
    }
  }
}
</script>
