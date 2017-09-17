<template>
  <div id="topbar">
    <div class="logo">
      VueResumer
    </div>
    <div class="actions">
      <el-button @click="startPreview">预览</el-button>
      <el-button type="primary">登录</el-button>
      <el-button>注册</el-button>
    </div>
  </div>
</template>

<style lang="scss">
  #topbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 8px;
    font-size: 20px;
  }
</style>

<script>
  export default {
    props: ['preview'],
    methods: {
      startPreview() {
        this.$emit('preview')
      }
    }
  }
</script>
