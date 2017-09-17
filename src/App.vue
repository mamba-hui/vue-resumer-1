<template>
  <div id="app">
    <Topbar class="topbar"/>
    <main>
      <Editor v-bind="resumer" class="editor"/>
      <Preview v-bind="resumer" class="preview"/>
    </main>
  </div>
</template>

<script>
  import Topbar from './components/Topbar.vue'
  import Editor from './components/Editor.vue'
  import Preview from './components/Preview.vue'

  export default {
    data() {
      return {
        resumer: {
          profile: {
            canAdd: false,
            title: '个人信息',
            content: [
              {
                name: {value: '', label: '姓名'},
                city: {value: '', label: '城市'},
                birthday: {value: '', label: '出生日期'}
              }
            ]
          },
          workHistory: {
            canAdd: true,
            title: '工作经历',
            content: [
              {
                company: {value: '', label: '公司'},
                workContent: {value: '', label: '工作内容'}
              }
            ]
          },
          studyHistory: {
            canAdd: true,
            title: '学习经历',
            content: [
              {
                school: {value: '', label: '学校'},
                duration: {value: '', label: '学期'},
                degree: {value: '', label: '学位'}
              }
            ]
          },
          project: {
            canAdd: true,
            title: '项目经历',
            content: [
              {
                projectName: {value: '', label: '项目名称'},
                projectContent: {value: '', label: '项目内容'}
              }
            ]
          },
          awards: {
            canAdd: true,
            title: '获奖情况',
            content: [
              {
                name: {value: '', label: '奖励详情'}
              }
            ]
          },
          contacts: {
            canAdd: false,
            title: '联系方式',
            content: [
              {
                qq: {value: '', label: 'qq'},
                weChat: {value: '', label: '微信'},
                phone: {value: '', label: '电话'},
                email: {value: '', label: '邮箱'}
              }
            ]
          }
        }
      }
    },
    components: {
      Topbar, Editor, Preview
    }
  }
</script>

<style lang="scss">
  html, body, #app {
    height: 100%;
  }
  .icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
  }
  #app {
    display: flex;
    flex-direction: column;
  }
  .topbar {
    box-shadow: 0 0 3px 3px rgba(0, 0, 0, .5);
  }
  main {
    display: flex;
    flex: 1;
    background-color: #ddd;
    > .editor, .preview {
      box-shadow: 0 0 3px 3px rgba(0, 0, 0, .5);
      border-radius: 5px;
      overflow: hidden;
      background-color: #fff;
    }
    > .editor {
      width: 40em;
      margin: 16px 8px 16px 16px;
    }
    > .preview {
      flex: 1;
      margin: 16px 16px 16px 8px;
    }
  }
</style>
