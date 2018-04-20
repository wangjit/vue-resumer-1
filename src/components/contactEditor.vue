<template>
  <div>
    <h2>联系方式</h2>
    <el-form>
     <el-form-item label="QQ">
       <el-input v-model="contact.QQ"></el-input>
     </el-form-item>
     <el-form-item label="微信">
       <el-input v-model="contact.Weichat"></el-input>
     </el-form-item>
     <el-form-item label="邮箱">
       <el-input v-model="contact.Email"></el-input>
     </el-form-item>
     <el-form-item label="手机">
       <el-input v-model="contact.Phone"></el-input>
     </el-form-item>
    </el-form>
  </div>
  
</template>

<script>
  export default {
    props: ['contact']
  }
</script>
