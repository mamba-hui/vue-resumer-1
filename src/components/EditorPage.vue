<template>
  <div>
    <h2>{{ info.title }}</h2>
    <el-form label-position="top">
      <div v-for="(item, index) in info.content" class="input-container" :key="index">
        <i v-if="info.canAdd && index > 0" class="el-icon-circle-close" @click="removeItem(index)"></i>
        <el-form-item v-for="(input, key) in item" :label="input.label" :key="index + key">
          <el-input v-model="input.value"></el-input>
        </el-form-item>
      </div>
      <div class="add-work">
        <el-button v-if="info.canAdd" type="primary" @click="addItem">添加{{ info.title }}</el-button>
      </div>
    </el-form>
  </div>
</template>

<script>
  export default {
    props: ['info'],
    methods: {
      addItem() {
        this.info.content.push(this.getOriginInput())
      },
      removeItem(index) {
        this.info.content.splice(index, 1)
      },
      getOriginInput() {
        let obj = {}
        Object.keys(this.info.content[0]).forEach((key) => {
          obj[key] = {}
          Object.keys(this.info.content[0][key]).forEach((subkey) => {
            obj[key][subkey] = this.info.content[0][key][subkey]
            obj[key]['value'] = ''
          })
        })
        return obj
      }
    }
  }
</script>
