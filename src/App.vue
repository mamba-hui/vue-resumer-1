<template>
  <div id="app">
    <Topbar class="topbar"/>
    <main>
      <Editor class="editor"/>
      <Preview class="preview"/>
    </main>
  </div>
</template>

<script>
  import Topbar from './components/Topbar.vue'
  import Editor from './components/Editor.vue'
  import Preview from './components/Preview.vue'

  export default {
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
