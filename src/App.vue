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
  #app {
    display: flex;
    flex-direction: column;
  }
  .topbar {
  }
  main {
    display: flex;
    flex: 1;
    > .editor {
      width: 20em;
    }
    > .preview {
      flex: 1;
    }
  }
</style>
