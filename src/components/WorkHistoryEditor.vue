<template>
  <div>
    <h2>工作经历</h2>
    <el-form label-position="top">
      <div v-for="(work, index) in workHistory" class="input-container">
        <i class="el-icon-circle-close" @click="removeWorkHistory(index)"></i>
        <el-form-item label="公司">
          <el-input v-model="work.company"></el-input>
        </el-form-item>
        <el-form-item label="工作内容">
          <el-input v-model="work.content"></el-input>
        </el-form-item>
      </div>
    </el-form>
    <div class="add-work">
      <el-button type="primary" @click="addWorkHistory">添加工作经历</el-button>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['workHistory'],
    methods: {
      addWorkHistory() {
        this.workHistory.push({
          company: '',
          content: ''
        })
      },
      removeWorkHistory(index) {
        this.workHistory.splice(index, 1)
      }
    }
  }
</script>
