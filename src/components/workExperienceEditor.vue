<template>
<div>
  <h2>工作经历</h2>
  <el-form>
    <div class="i-ct" v-for="(work, index) in workExperience">
      <el-form-item label="公司">
        <el-input v-model="work.company"></el-input>
      </el-form-item>
      <el-form-item label="工作内容">
        <el-input v-model="work.content"></el-input>
      </el-form-item>
      <i class="el-icon-remove" v-on:click="removeWorkExperience(index)"></i>
      <hr style="margin-bottom: 10px; ">
    </div>
    <el-button v-on:click="addWorkExperience">添加一项</el-button>
  </el-form>
</div>
</template>

<script>
export default {
  props: ['workExperience'],
  methods: {
    addWorkExperience() {
      this.workExperience.push({
        company: '',
        content: ''
      })
    },
    removeWorkExperience(index) {
      this.workExperience.splice(index, 1)
    }
  }
}
</script>
