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
        <editor-page :info="profile"/>
      </li>
      <li v-show="currentTab === 1">
        <editor-page :info="workHistory"/>
      </li>
      <li v-show="currentTab === 2">
        <editor-page :info="studyHistory"/>
      </li>
      <li v-show="currentTab === 3">
        <editor-page :info="project"/>
      </li>
      <li v-show="currentTab === 4">
        <editor-page :info="awards"/>
      </li>
      <li v-show="currentTab === 5">
        <editor-page :info="contacts"/>
      </li>
    </ol>
  </div>
</template>

<script>
  import EditorPage from './EditorPage.vue'

  export default {
    props: ['profile', 'workHistory', 'studyHistory', 'project', 'awards', 'contacts'],
    components: {
      EditorPage
    },
    data() {
      return {
        tabLength: 6,
        currentTab: 0,
        icons: [
          'icon-credentials_icon',
          'icon-gongwenbao',
          'icon-book',
          'icon-heart',
          'icon-trophy',
          'icon-3-copy'
        ],

      }
    },
    methods: {}
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
