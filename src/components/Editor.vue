<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="(item, index) in Array.apply(null, {length: tabLength})" :class="{active: currentTab === index}"
            @click="currentTab=index">
          <svg class="icon">
            <use :xlink:href="`#${icons[index]}`"></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panels">
      <li v-show="currentTab === 0">
        <h2>个人信息</h2>
        <el-form label-position="top">
          <el-form-item label="姓名：">
            <el-input v-model="profile.name"></el-input>
          </el-form-item>
          <el-form-item label="城市：">
            <el-input v-model="profile.city"></el-input>
          </el-form-item>
          <el-form-item label="出生日期：">
            <el-input v-model="profile.birthday"></el-input>
          </el-form-item>
        </el-form>
      </li>
      <li v-show="currentTab === 1">
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
      </li>
      <li v-show="currentTab === 2">
        <h2>学习经历</h2>
      </li>
      <li v-show="currentTab === 3">
        <h2>项目经历</h2>
      </li>
      <li v-show="currentTab === 4">
        <h2>获奖情况</h2>
      </li>
      <li v-show="currentTab === 5">
        <h2>联系方式</h2>
      </li>
    </ol>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        tabLength: 6,
        currentTab: 0,
        icons: [
          'icon-credentials_icon',
          'icon-book',
          'icon-gongwenbao',
          'icon-3-copy',
          'icon-trophy',
          'icon-heart'
        ],
        profile: {
          name: '',
          city: '',
          birthday: ''
        },
        workHistory: [
          {
            company: '',
            content: ''
          }
        ]
      }
    },
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

<style lang="scss">
  #editor {
    display: flex;
    > nav {
      width: 80px;
      background-color: #000;
      > ol > li {
        padding: 16px 0;
        text-align: center;
        > .icon {
          width: 24px;
          height: 24px;
          fill: #fff;
        }
        &.active {
          background-color: #fff;
          > .icon {
            fill: #000;
          }
        }
      }
    }
    > .panels {
      flex: 1;
      overflow: auto;
      > li {
        padding: 16px 32px;
        > h2 {
          margin-bottom: 16px;
        }
        .input-container {
          position: relative;
          border-top: 1px solid #ddd;
          padding-top: 16px;
          > i {
            position: absolute;
            top: 16px;
            right: 5px;
            &:hover {
              color: #666;
            }
          }
        }
        .add-work {
          margin-top: 16px;
          text-align: center;
        }
      }
    }

  }
</style>
