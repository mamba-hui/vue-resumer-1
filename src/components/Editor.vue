<template>
  <div id="editor">
    <nav>
      <ol>
        <li v-for="(item, index) in Array.apply(null, {length: tabLength})" :class="{active: currentTab === index}" @click="currentTab=index">
          <svg class="icon">
            <use :xlink:href="`#${icons[index]}`"></use>
          </svg>
        </li>
      </ol>
    </nav>
    <ol class="panels">
      <li v-for="(item, index) in new Array(tabLength)" :class="{active: currentTab === index}">
        Tab{{ index + 1 }}
      </li>
    </ol>
  </div>
</template>

<script>
  export default {
    data(){
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
        ]
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
    .panels {
      > li {
        display: none;
        &.active {
          display: block;
        }
      }
    }
  }
</style>
